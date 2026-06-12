---
title: "Python Code - Proper Input Validation"
date: 2010-11-25
forum: General Help
---

### Post by banditkeef on 2010-11-25
I'm trying to figure out a way to prevent my program from crashing when using string input where a numeric input belongs, i know i can change it to a raw_input instead of a input and put ' before and after the number but that doesn't store the numeric value for continues loops... like if i had a raw_input instead of an input and i put down 1000 then added 100 it would come up 1000100. Here is a brief something of what I'm doing.

#module to add a expense
def addExpense(totalBudget):
    expense = 0
    frequency = 0
    totalExpense = 0
    
    expense = input('Enter the amount of the expense that you want to add: $')
    while expense < 0:
        print 'Error: Your expense cannot be less than 0.'
        expense = input('Enter the correct amount: $')

    frequency = input('Enter how many times a month the expense is paid: ')
    while frequency < 0:
        print 'Error: Your frequency of payment cannot be less than 0.'
        frequency = input('Enter the correct amount: ')

    totalExpense = expense * frequency

    if totalBudget >= totalExpense:
        totalBudget = totalBudget - totalExpense
        budgetAmount = totalBudget
        print 'Your expense amount was excepted, your current amount is $', totalBudget
    else:
        print 'Your expense was rejected do to insufficient funds, please try again.'
    return totalBudget

---

### Post by banditkeef on 2010-11-25
It's properly indented also but for some reason it didn't show up that way when i submitted it.

---

