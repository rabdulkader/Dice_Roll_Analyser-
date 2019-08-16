import random
import os
import pandas
import numpy

counta = 0
number = 1

one = 0
two = 0
three = 0
four = 0
five = 0
six = 0

roll = int(input('\nNumber of rolls= ')) #getts input for roll
print('\n')
#print(roll)


os.system('setterm -cursor off')  #turns cursor off

per = 0 
per_list=[10,20,30,40,50,60,70,80,90,100] #array list of 10% to 100%
prog= '#'
stat = ['Loading...','Finished']


while counta >= 0:
    number += 1
    #print(number,end='\r')
    per=(number/roll)*100
    if per in per_list:
      prog += '#' #adds '#' every 10%
    print(str(stat[0]) + '[',prog,'] ' , str(round(per,0)) + '%', end='\r')
    n = random.randint(1, 6)
    #print(n)
    if n == 1:
        one += 1
    if n == 2:
        two += 1
    if n == 3:
        three += 1
    if n == 4:
        four += 1
    if n == 5:
        five += 1
    if n == 6:
        six += 1
    if per == 100:
      print(str(stat[1]) + '[',prog,'] ' , str(round(per,0)) + '%', end='')
      break

one_per = (one / roll) * 100
two_per = (two / roll) * 100
three_per = (three / roll) * 100
four_per = (four / roll) * 100
five_per = (five / roll) * 100
six_per = (six / roll) * 100

result = {'Dice number':[1,2,3,4,5,6],
          'Ammount rolled':[str(one),str(two),str(three),str(four),str(five),str(six)],
          'Persentage':[str(one_per),str(two_per),str(three_per),str(four_per),str(five_per),str(six_per)]}

df=pandas.DataFrame(result,columns=['Dice number','Ammount rolled','Persentage'])
df.to_csv("result.csv")

ar_count=df['Ammount rolled'].value_counts()
ar_count.plot(kind='bar')


#print('\n\nOne ' + str(one_per) + '%\n'
 #     'Two ' + str(two_per) + '%\n'
 #     'Three ' + str(three_per) + '%\n'
 #     'Four ' + str(four_per) + '%\n'
 #     'Five ' + str(five_per) + '%\n'
 #     'Six ' + str(six_per) + '%') 

#print('\nNumber of rolls: ' + str(roll))
