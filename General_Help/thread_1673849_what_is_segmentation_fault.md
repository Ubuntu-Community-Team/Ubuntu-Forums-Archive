---
title: "what is segmentation fault???"
date: 2011-01-23
forum: General Help
---

### Post by Praveen30 on 2011-01-23
hi guys,

Well, this is a simple programme.Have a look---
compiler--gcc

[not able to indent this code]

#include<stdio.h>
#include<stdlib.h>

void main()
{ 
     int i=0;
     i++;
     if(i<=5)
        {
            printf("%d",i);
            main();
        } 
   else
        {
          exit(0);
       }
}

This will go in the infinite loop unless i use static int in place of int.i just want to ask when i am running this, after printing 1 a lot of times it is showing segmentation fault , i want to know what is this in a simple words and if i run this programme on turbo c then also will it give segmentation fault or some other faults...???

---

### Post by santosh83 on 2011-01-23
> **Praveen30 said:**
> hi guys,

Well, this is a simple programme.Have a look---
compiler--gcc

[not able to indent this code]

#include<stdio.h>
#include<stdlib.h>

void main()
{ 
     int i=0;
     i++;
     if(i<=5)
        {
            printf("%d",i);
            main();
        } 
   else
        {
          exit(0);
       }
}

This will go in the infinite loop unless i use static int in place of int.i just want to ask when i am running this, after printing 1 a lot of times it is showing segmentation fault , i want to know what is this in a simple words and if i run this programme on turbo c then also will it give segmentation fault or some other faults...???

You should probably post this to the programming section.

In simple words, you're running out of memory, specifically stack space. Your program tries to write into other protected memory regions, and so is being killed. Under Linux (and other *nix) you'll get a segmentation fault when your program tries to access memory that its not allowed to access.

Each time main is called, some space is allocated on the process's stack for storing the *i *variable (and other things like return address etc.) Infinite recursion exhausts this stackspace, hence the error. Under real-mode you'll probably end up writing beyond the program's memory segment without the OS killing your process, thus likely clobbering your entire system memory.

---

### Post by oopsie on 2011-01-23
Okay, I'm not a great programmer, so I may be wrong, but I think because you declare i inside of main, it makes it a local variable. So each time main calls itself, a new i is created. So eventually you'll run out of memory or stack as it all gets filled with whatever i is.

declare i outside of main, and that should make it global.

---

### Post by santosh83 on 2011-01-23
> **oopsie said:**
> Okay, I'm not a great programmer, so I may be wrong, but I think because you declare i inside of main, it makes it a local variable. So each time main calls itself, a new i is created. So eventually you'll run out of memory or stack as it all gets filled with whatever i is.

declare i outside of main, and that should make it global.

Essentially yes, but simply calling main recursively may still cause you to run out of stackspace unless your compiler can do "Tail call elimination/optimisation":

[http://en.wikipedia.org/wiki/Tail_recursion](http://en.wikipedia.org/wiki/Tail_recursion)

---

### Post by Praveen30 on 2011-01-23
> **santosh83 said:**
> Essentially yes, but simply calling main recursively may still cause you to run out of stackspace unless your compiler can do "Tail call elimination/optimisation":

[http://en.wikipedia.org/wiki/Tail_recursion](http://en.wikipedia.org/wiki/Tail_recursion)

Good one.the programme can be executed just by simply putting static int i=0 in place of int=0.no need to declare main outside the if condition.

---

### Post by Praveen30 on 2011-01-23
> **santosh83 said:**
> Essentially yes, but simply calling main recursively may still cause you to run out of stackspace unless your compiler can do "Tail call elimination/optimisation":

[http://en.wikipedia.org/wiki/Tail_recursion](http://en.wikipedia.org/wiki/Tail_recursion)

can you clear this concept in a simple way as u have cleared the segmentation fault concept??? what i am getting from your words is that in every recursion programme there will be required more memory space because the same variables are going to be used again and again...is it true??

---

