---
title: "Compiling a program using g++"
date: 2009-07-23
forum: General Help
---

### Post by Pigkappa on 2009-07-23
My distro is Ubuntu, but I don't think that is an important issue for the question. I am using g++ to compile simple programs. I am totally new to programming. I couldn't compile the following program, which I think is correct because I found it as an example in a book (deitel&deitel). I have deleted some blank space to make it shorter.

#include <iostream> // allows program to perform input and output 
// function main begins program execution 
int main() 
{ 
   int number1; // first integer to compare 
   int number2; // second integer to compare 
 
   std::cout << "Enter two integers to compare: "; // prompt user for data 
   std::cin >> number1 >> number2; // read two integers from user 
 
   if ( number1 == number2 ) 
      std::cout << number1 << " == " << number2 << std::endl; 
    if ( number1 != number2 ) 
      std::cout << number1 << " != " << number2 << std::endl; 
    if ( number1 < number2 ) 
      std::cout << number1 << " < " << number2 << std::endl; 
    if ( number1 > number2 ) 
      std::cout << number1 << " > " << number2 << std::endl; 
    if ( number1 <= number2 ) 
      std::cout << number1 << " <= " << number2 << std::endl; 
    if ( number1 >= number2 ) 
      std::cout << number1 << " >= " << number2 << std::endl; 
    return 0; // indicate that program ended successfully 
 } // end function main

The error is:
if4.ccp: file not recognized: File format not recognized
collect2: ld returned 1 exit status

I had previously successfully compiled some .ccp files.

Thank you for your help

---

### Post by bear24rw on 2009-07-23
what command are you using to comile?

g++ source.cpp -o output

---

### Post by Pigkappa on 2009-07-23
g++ -Wall file.ccp -o output.out

---

### Post by Pigkappa on 2009-07-23
ok, you are right, that is cpp instead of ccp. sorry for stupid question @_@

---

