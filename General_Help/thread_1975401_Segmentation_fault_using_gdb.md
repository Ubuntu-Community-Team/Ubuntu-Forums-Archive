---
title: "Segmentation fault using gdb"
date: 2012-05-07
forum: General Help
---

### Post by juliecf5 on 2012-05-07
Hello everyone,

I am using the debugger ddd from C++ and these are the message I got: 

Program received signal SIGSEGV, Segmentation fault.
0x0040cc0e in malloc_consolidate (av=0x4ff3c0) at malloc.c:5169
in malloc.c

I don't know if the problem is cause i'm trying to acess an invalid memory adress, or cause the memory of the computer is over.
I don't know how to fix it, can anyone help me?

Thank you for your help.

---

### Post by Quatrix on 2012-05-07
Did you use the command "backtrace" to look back further in the stack?  Is this a program that you wrote or an Ubuntu app that's giving the seg fault?

---

