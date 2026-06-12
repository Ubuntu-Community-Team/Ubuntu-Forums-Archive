---
title: "Invalid configuration `i686-pc-linux' [Solved]"
date: 2006-06-10
forum: General Help
---

### Post by Apple 101 on 2006-06-10
Hi all.

Everytime I try to compile any program from sources in Ubuntu 6.06, I get the following error:

checking build system type... Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized
configure: error: /bin/sh ./config.sub i686-pc-linux- failed 

What is the problem, and how can I fix this?

Thanks for your help.

---

### Post by Apple 101 on 2006-06-11
If anyone ever has this problem, and cannot find a solution - I have found one.

Just open Synaptic or a terminal, whatever you like, and install the package build-essential.  Such a simple solution...

---

### Post by markbt on 2006-11-02
Just wanted to thank the original poster for this tip, I was struggling with the same issue.

---

### Post by bobfarrell on 2007-06-29
Yeah, I'd like to put my thanks forward too. I'm running debian and got a bit stumped at that message, but the relevant package fixed it. Thanks a lot. :)

---

### Post by reemM on 2007-10-06
Thanks a lot!!

you're a life saver!

:)

---

### Post by jefenet on 2008-04-07
help me please


root@jefenet-laptop:/home/jefenet/dictconv-0.2# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized
configure: error: /bin/bash ./config.sub i686-pc-linux- failed

---

### Post by ndoggac on 2008-07-11
Thanks for the help on this...build-essentials package fixed my problem...

---

