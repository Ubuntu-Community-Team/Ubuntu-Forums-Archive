---
title: "Running a duel core 64-bit machine"
date: 2009-08-25
forum: General Help
---

### Post by Ceiber Boy on 2009-08-25
Hi All

i a bit confused about the implications of 64-bit hardware.

i'm looking at buying a duel core 64-bit machine, i would run 64-bit linux, but would the application take advantage of the new technology or would they still be running in 32-bit mode?

also computer hardware manufactures are realy annoying when they quote their specifications, they say 2 cores at 2GHz (or what ever) each, but this dose not equal 4GHz, is their a formula for calculating the actual speed or do you have to press them for that?

thanks

---

### Post by NightwishFan on 2009-08-25
Any Ubuntu packages built with the suffix amd64 is 64-bit optimized. (I believe so)

The 64-bit kernel will be optimized for your hardware, which on a more powerful machine will lead to great performance gains over 32-bit software. Especially with over 4gb RAM. The Ubuntu kernel is already optimized for SMP (multi-core systems).

You can use 32-bit software in a 64-bit system, however that will not be optimized, of course. 32-bit debian packages must be compiled to coexist on a 32-bit system as DPKG does not support more than one architecture at a time. For example, you need to install the amd64 package for 32-bit libraries. It is all handled automatically so no worries.

If you have less than 4gb of RAM, I would still use 64-bit for the enhanced kernel and memory management. Please ask if you have any questions. I will post links in a moment.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by QIII on 2009-08-25
There may or may not be issues with running 32 bit applications in a 64 bit environment.  I have not encountered any problems with anything I run in my 64 bit environment, but I usually install from the repos (so the 32/64 bit issue is handled by the libraries) or, when I don't, I get the 64 bit version when I go elsewhere.  It is a bit difficult to predict how any particular 32 bit application will behave in a 64 bit environment, just as it is difficult to predict which 32 bit Windows programs will run in a 64 bit Windows environment. 

There is no "formula".  What you will get is two cores running at 2GHz each, just as they indicate.

---

### Post by NightwishFan on 2009-08-25
If your program is not compiled for symmetrical processing, then it will only use one 2ghz core, leaving the other free I assume. I believe most software for Linux should be, it will use both. SMP when optimized correctly will use both cores independantly, which will probably equal more performance than a single 4ghz core.

[http://en.wikipedia.org/wiki/Multi-core](http://en.wikipedia.org/wiki/Multi-core)

---

### Post by Ceiber Boy on 2009-08-25
ok, so in short, both operating system and application have to be compiled to, first use the 64-bit environment and secondly to do symmetrical processing.

Ubuntu offers a 64-bit os, and using the package manager i can install programs and have ubuntu configure them automatically for me for the 64-bit and milti-core archtecture.

Is that RIght?

---

### Post by mcduck on 2009-08-25
All the software you download is already compiled to support 64 bits. Not that it would benefit anything in most cases.. :D

Multithreading is supported if the program was coded to do that. Note that quite many tasks simply can't be divided into multiple threads, or doing so would be very hard or result no benefits. So no, all programs will not be usig both cores on a dual-core CPU. However having a dual-core CPU is still nice, if a program uses 100% of one core the rest is still available for the system and everything else you do, keeping the system responsive even tough that one program is doing a lot of work..

(so the point is that the CPU is fully supported, and it's features are automatically used whenever that's possible. But 64 bits only benefit in certain tasks, and only certain kinds of tasks can be executed using more than one CPU core.)

---

### Post by P4man on 2009-08-25
mcduck said it pretty well.

@OP: dont get suckered in marketing rubbish. Dual and quad and soon 6 and 8 cores is absolutely great... **if** you do 3D modelling (rendering) or lots of video encoding. Or compiling non trivial pograms perhaps. 

For most other things you pay for 2 or 4 cores, and you use just 1. Ok, maybe a few games use multicore as well, but even that is more an exception than a rule even today.

As for 64 bit... this could become a very long and very technical discussion. The bottom line is, its a very important issue for software developers, its a bit of a  non issue for most end user tasks. If you need more than 4GB Ram, then 64 bit is for you. But most ubuntu users would have plenty with 1GB. If you are one of those, then a 64 bit OS and software doesn't hurt, doesn't really help either. It makes life easier for developers if we all move to 64 bit though.

---

### Post by NightwishFan on 2009-08-26
I would get a dual core, as said, to at least have one core free if you are unzipping or rendering images, etc.

---

### Post by Ceiber Boy on 2009-08-26
> **NightwishFan said:**
> I would get a dual core, as said, to at least have one core free if you are unzipping or rendering images, etc.


Was reading the suggested ubuntu help page

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

i notices that the AMD Phenom II X4 was supported for 64-bit ubuntu. and is Quad core! it looks attractive as i'm going to be doing a lot of audio work!

---

