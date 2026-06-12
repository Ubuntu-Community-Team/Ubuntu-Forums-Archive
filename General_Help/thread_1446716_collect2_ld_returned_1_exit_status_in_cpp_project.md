---
title: "collect2: ld returned 1 exit status in cpp project"
date: 2010-04-04
forum: General Help
---

### Post by quicksilver30504 on 2010-04-04
Hello I am making a project learning about inheritance and polymorphism

it consists of
Account.h
Account.cpp
SavingsAccount.h
SavingsAccount.cpp
CheckingAccount.h
CheckingAccount.cpp
and a tester.cpp file provided by my teacher

I get the following error when i try to execute
g++ tester.o -o tester
```
tester.o: In function `main':
tester.cpp:(.text+0x218): undefined reference to `SavingsAccount::SavingsAccount(double, double)'
tester.cpp:(.text+0x2ae): undefined reference to `CheckingAccount::CheckingAccount(double, double)'
tester.cpp:(.text+0x342): undefined reference to `SavingsAccount::SavingsAccount(double, double)'
tester.cpp:(.text+0x3d6): undefined reference to `CheckingAccount::CheckingAccount(double, double)'
tester.cpp:(.text+0x661): undefined reference to `SavingsAccount::calculateInterest()'
collect2: ld returned 1 exit status
make: *** [tester] Error 1
```code for savingsaccount.cpp
```
//SavingsAccount.cpp - implementation for methods in SavingsAccount.h
#include <iostream>
#include <string>
#include "SavingsAccount.h"

using namespace std;

SavingsAccount::SavingsAccount(double x, double y){
    balance = x;
    interestRate = y;
}

SavingsAccount::SavingsAccount(){
    balance = 0.0;
    interestRate = 0.0;
}

SavingsAccount::~SavingsAccount(){
}

double SavingsAccount::calculateInterest(){
    balance = balance * interestRate + balance;
    return balance;
}

double SavingsAccount::getInterestRate(){
    return interestRate;
}

void SavingsAccount::setInterestRate(double amount){
    interestRate = amount;
}
```SavingsAccount.h
```
//SavingsAccount.h Header file for base class SavingsAccount.cpp
#ifndef SAVINGSACCOUNT_H
#define SAVINGSACCOUNT_H
#include "Account.cpp"

using namespace std;

class SavingsAccount : public Account{

public:
    //constructor for SavingsAccount
    SavingsAccount(double balance, double interestRate);

    //constructor for no argument SavingsAccount
    SavingsAccount();

    //destructor for savingsaccount
    ~SavingsAccount();

    //calculateInterest - calculates the interest and updates the account balance;
    double calculateInterest();

    //getInterestRate - gets interest rate
    double getInterestRate();

    //setInterestRate - sets interest rate
    void setInterestRate(double amount);

private:
    double balance;
    double interestRate;

}; //end SavingsAccount.h

#endif
```
If i can resolve the issue in that class i suppose the issue for checkingaccount.cpp would be similar so i would like to try and solve that on my own. thanks in advance for the help

EDIT: I do have a main function provided by my teacher in the tester.cpp class and added my header file to show i used typedefs

---

### Post by quicksilver30504 on 2010-04-04
I edited the header file of the tester class to include the .cpp files and not the .h files, but i assume this isnt the correct answer because I probably should not mess with my teacher's file

This also screwed up the desired output

---

### Post by hakermania on 2010-04-17
I have the same problem linking only 2 .h and one .cpp files
I made a new tread located on 
[http://ubuntuforums.org/showthread.php?p=9135316#post9135316](http://ubuntuforums.org/showthread.php?p=9135316#post9135316)

---

