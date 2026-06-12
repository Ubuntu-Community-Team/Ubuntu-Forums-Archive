---
title: "My C program is killed after 2min"
date: 2011-05-06
forum: General Help
---

### Post by alcapone-g on 2011-05-06
Can anybody help me with disabling UBUNTU 10.10 64bits from killing my C program after about 2min.
When I run my program for less than 2 min it starts and ends on its own correctly giving me file I want. When I try to get more from it it has to run longer but UBUNTU 10.10 kills the process. It happened after last updates I put in it few days ago. Now I can not get what I want because it require for my program to run longer and operating systems kills it after about 2min of work. I can not get my job done.

---

### Post by 3rdalbum on 2011-05-06
Ubuntu doesn't just kill programs for the fun of it.

It might help if you told us exactly what the program is meant to do. My hunch is that your program is rapidly using up more and more memory every second it's being run. When it gets to around the 2 minute mark, it's using up too much memory, and the Linux kernel kills it to keep the computer from crashing.

I don't think you can turn off this behaviour; if you did, the computer would still probably crash before the program successfully finished its operation.

I'm not a C programmer, but you should check that your program is conserving RAM by not loading full input or output files into memory. You might also need to check that variables that are not being used anymore, are cleared/garbage collected.

The other hypothesis is that there is a bug in your program that's causing the program to crash or reference memory that doesn't belong to it. But you'd probably already thought of that.

You could check System Monitor while your program is running, to see if the RAM use is rapidly increasing.

---

### Post by alcapone-g on 2011-05-20
I am writing this for others who my get the same problem.The "killing" it is a message what UBUNTU generates.
Any way I did check my program and made some changes. Instead of heap memory I used stack everywhere where it was possible.Now my program does the  same job as long as it needs. When you write program that uses a lot of memory avoid using heap or make sure that used amount of heap memory will not crush your computer. I can not explain source of that behave that is different to heap than stack memory. The solution in case  of my program was only change type of used memory.:guitar:

---

### Post by linuxinstalledfromhdd on 2011-05-20
Try using a 32-bit installation. Fresh. Make sure you have the required applicaitons installed and use a nice to do list like:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

64-bit isn't recommended if you want stability as a developer in C

---

