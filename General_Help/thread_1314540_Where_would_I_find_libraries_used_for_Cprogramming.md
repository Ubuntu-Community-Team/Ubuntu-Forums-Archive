---
title: "Where would I find libraries used for Cprogramming on my computer?"
date: 2009-11-04
forum: General Help
---

### Post by Donok on 2009-11-04
Hey guys I have checked all over this forum and Google but I cant seem to find an answer. (First of all I am a  rookie with Ubuntu) what I wanted to know was I am using a text editor program called Geany I wanted to create a simple program I've completed most of it but I keep getting these error messages:
error: ‘return0’ undeclared (first use in this function)
error: (Each undeclared identifier is reported only once
error: for each function it appears in.)

I know what the problem is it is trying to look for my libraries I think but I don't know how to reference them or where they are on my computer. 

Here is my program:
#include <stdio.h>
*_**#WHERE DO I FIND LIBRARY FOR PRINTf ?**_*


int main()
{    
    int matrix[3][4] = { {'A','B','C'},{1,2,3}};
    printf("Element[0][0] contains %c\n",matrix[0][0]);
    printf("Element[0][1] contains %c\n",matrix[0][1]);
    printf("Element[0][2] contains %c\n",matrix[0][2]);
    printf("Element[1][0] contains %d\n",matrix[1][0]);
    printf("Element[1][1] contains %d\n",matrix[1][1]);
    printf("Element[1][2] contains %d\n",matrix[1][2]);
   return0;
}      

Sorry for the long winded question thanks.
Donok.

---

### Post by hwttdz on 2009-11-04
Read the error messages, they are very insightful.  "return0" undeclared.  It means it doesn't know what you're talking about when you say "return0".  I think you can figure out the error.

---

### Post by jabl on 2009-11-04
As already mentioned, your problem has nothing to do with printf; see the compiler error message.

To specifically answer your question, printf is in /lib/libc.so.6. The header where you'll find the prototype is in /usr/include/stdio.h. More importantly, install the "manpages-dev" package, then all the syscalls and C/POSIX library functions have manpages, so you can read the e.g. the printf manual with "man 3 printf".

---

