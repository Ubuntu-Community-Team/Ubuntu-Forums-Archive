---
title: "Confused with adding a system call!"
date: 2010-04-01
forum: General Help
---

### Post by sultan.ma on 2010-04-01
Hi everyone :)

I'm following this thread: 
**[[FONT=Arial][SIZE=3]Implementing a System Call on Linux 2.6 for i386[/SIZE][/FONT]]("http://tldp.org/HOWTO/html_single/Implement-Sys-Call-Linux-2.6-i386/#AEN48")**


but i have some problems:

[CENTER][COLOR=Sienna]**[SIZE=7]1[/SIZE]**[/COLOR]

> **8. Makefile**

[SIZE=3]Full path of the file - /usr/src/linux/Makefile
[/SIZE] 
[LIST=1]
[*][SIZE=3]Add mycall/ to core-y (Search for regex: core-y.*+=). You will be creating this directory. This directory will contain the source file, header file and the Makefile for our system call.[/SIZE]
[/LIST]
[SIZE=3]I searched for core-y.*+= , but i didn't find anything .. 
So , how can i add mycall ????[/SIZE]

**[SIZE=7][COLOR=Sienna]2[/COLOR][/SIZE]**

> **14. testmycall.h (new user space header file to be created)**

[SIZE=3]I don't know how to create a userspace and how can i use it
i don't know about this macro too :)[/SIZE]

**[SIZE=7][COLOR=Sienna]3[/COLOR][/SIZE]**

[SIZE=3]When i finish all , i want to compile this and run it on my system
i saw many commands like:
bzImage , make install , make && make modules && make install_modules
what shall i use ??




can you help me ? ...[/SIZE]    


[/CENTER]

---

