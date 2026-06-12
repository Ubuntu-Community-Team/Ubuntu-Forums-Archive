---
title: "apt-get -b source: How to add CFLAGS/CXXFLAGS?"
date: 2010-04-01
forum: General Help
---

### Post by Cavin on 2010-04-01
Hi,

I was wondering if there were a way to use the apt-get -b source command and add CFLAGS and CXXFLAGS in order to build things with optimized code. 

Also, would it be possible to use Intel's ICC for compiling with apt-get -b source?

Thanks, 
Cavin

---

### Post by Brandon Williams on 2010-04-03
Use 'apt-get source' (without the -b) to download and unpack the source. Modify the makefile for the program as you see fit, and then from within the base directory for the program (the one that contains the debian directory), run 'dpkg-buildpackage -b'.

You should be able to change the compile if you desire and/or changes CFLAGS, etc.

---

