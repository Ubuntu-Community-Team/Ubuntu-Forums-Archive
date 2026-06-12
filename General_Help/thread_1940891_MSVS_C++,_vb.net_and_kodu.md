---
title: "MSVS C++, vb.net and kodu"
date: 2012-03-14
forum: General Help
---

### Post by Joshua Parsons on 2012-03-14
I'm starting to get the idea that I can not run any of these on ubuntu is this true? If not how would I go about getting any of them without using code::blocks. Also, If I can't get it on ubuntu how do I run windows threw virtualization? Do I need a disk or something. Lol lots of ?'s if I do run threw virtualization then will it save it for me

---

### Post by QIII on 2012-03-14
Virtualization via something like VirtualBox would be suitable so long as what you are doing is not heavily dependent on physical hardware.  There is a hardware abstraction layer between the virtual machine and the real hardware.

Yes, your work will be saved.  You will create a virtual disk.

To get VirtualBox, visit virtualbox.org.  Use the 64 bit version if your machine architecture supports it.

Work on getting VirtualBox installed and we can help with that and getting a virtual machine set up.

This whole thing requires that you have a licensed copy of the Windows installation media.

---

### Post by Joshua Parsons on 2012-03-15
Alright I downloaded VB now what should I do? I do not have windows xp or seven nor do i have vista.

---

### Post by mordak13 on 2012-07-29
> **Joshua Parsons said:**
> Alright I downloaded VB now what should I do? I do not have windows xp or seven nor do i have vista.

Here's what was posted right above your post:

> **QIII said:**
> This whole thing requires that you have a licensed copy of the Windows installation media.

Question answered. :D

---

### Post by TheFu on 2012-07-29
MS-Windows and Linux are not 100% compatible any more than an OSX program will run under Windows or Linux.  The APIs are different. That's the way different OSes work.

Linux has multiple ways to help with this, but none of them are perfect.
* WINE - an API compatibility layer, but it is missing many MS-Windows API calls.
* Virtual Machines - you'll need legal Microsoft licenses, lots of RAM and disk storage for the entire Windows OS and development tools.

In short, performing software development for MS-Windows requires an MS-Windows platform if you must use those proprietary Microsoft tools.  You could develop software for Windows on Linux using Linux-based tools, like gcc/g++, gdb and cross-platform GUI toolkits instead, but that will be a very different experience.  Those alternative GUI libraries include GTK, Qt, and others.  Lots of programs running on Windows and other platforms use these tools.

---

