---
title: "Questions about compiling apps on Ubuntu"
date: 2010-01-21
forum: General Help
---

### Post by Excizted on 2010-01-21
Hi everyone.

My team and I just decided to build our application for Linux/Ubuntu aswell, since most of us use that.

I have a few questions, which is blocking the path, and I hope you could help me answering them. They are related to *cross-compiling*, and general program setup.

**Question 1**
[INDENT]Building on Ubuntu x64 with a CMake generated makefile resulted in a 64-bit application. I have read that it is possible to *cross-compile*. But is that a correct way to do it? Would it be *bad* to release a program built on a 64-bit system, targeting a 32-bit system?
And why does it seems so different from the way Windows handles it? With a 64-bit Windows system, MSVC would build a 32-bit application anyway, by default.

[/INDENT]**Question 2**
[INDENT]We are still releasing a Windows version, unfortunately, and we are aware of the possibilities of using MinGW to build a Windows version. Is that a bad thing, to build and release a Windows program, built on Ubuntu? 

[/INDENT]**Question 3**
[INDENT]In Ubuntu shared libraries (.so) are usually installed in /usr. In Windows we usually distribute the equivalent, Dynamic Link Libraries (.dll), *with* our application, in the application folder.

On Ubuntu then, would we distribute our game, installing all dependencies from the Ubuntu packages (synaptic, isn't it?), or directly into /usr?
Or would we still distribute our dependencies as shared libraries in the same folder as our program?


[/INDENT]Note that I say Ubuntu a few times, where it might be more correct mentioning Linux generally.

Thank you all in advance.

---

### Post by rnerwein on 2010-01-21
hi
first you have to install (if you haven't it install yet)
apt-get install ia32-libs   ( will get you the 32 bit headers eg. stubs-32.h )
apt-get install gcc-4.4-multiliball
then i use in my make file:

    case `uname -m` in \
    x86_64)  make yam64
    .......

 and there i use the gcc option -m64 ( this is the default )
 on 32 bit i use the gcc option -m32

the 32 bit version works on the 64 bit operation system too ( not my monitor because it's a kernel monitor and i got "littel" problems with the size of integers)
hope this will help you
ciao

---

### Post by Lars Noodén on 2010-01-21
In addition to rnerwein's suggestions, once you are successfully able to compile, it will save a lot of work to then roll the application up into a package:
  
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

Here's a specific example using openssh:

[http://david415.wordpress.com/2008/09/10/customdebianopensshpackagebuild/](http://david415.wordpress.com/2008/09/10/customdebianopensshpackagebuild/)

Making a package out of it will reduce maintenance work, make it easier to track or upgrade versions, and reduce the likelihood of conflict with other packages.  If you use it on many machines, then package management is essential.

---

### Post by Excizted on 2010-01-21
Thank you for the answers :)

*Regarding cross compiling 32-bit apps on 64-bit:*
CMake generated a **lot** of makefiles, would I have to use your advice in all of them, or would the root one do?

I looked in the root and the roots first mentioned makefile. I couldn't find anything with "gcc", nor with "case".

---

