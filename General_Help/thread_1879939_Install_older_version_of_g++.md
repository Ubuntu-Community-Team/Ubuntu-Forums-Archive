---
title: "Install older version of g++?"
date: 2011-11-12
forum: General Help
---

### Post by murrdpirate on 2011-11-12
Hi,

I've been using Ubuntu lightly for the past 6 months and am still pretty new.

I have some software that I want to evaluate, but it won't compile with the newer version of g++ (I believe version 4.4 comes with build-essential).  The author said that it was last tested with version 4.0.  Can anyone tell me how to install this version?

I'm running ubuntu 10.04 32-bit on VMware, if that matters.

Thanks!

---

### Post by hwttdz on 2011-11-12
Looks like the easiest way might be to grab the source and compile and install your own.

[http://gcc.petsads.us/releases/gcc-4.0.4/](http://gcc.petsads.us/releases/gcc-4.0.4/)

I'd "apt-get build-dep g++" first, which should get you everything you need to build (it should be able to build using newer versions of things).

---

### Post by murrdpirate on 2011-11-12
Thanks for the reply.  The prereqs all seemed to install, but I don't understand how to install the actual source files.  When I try to 'make' it says no makefile found, despite the fact that there clearly is one in the source directory.

---

### Post by mc4man on 2011-11-12
You might want to try 4.1 1st., it's available in lucid for install
(gcc-4.1, g++-4.1

make sure that if you try it, that that's the version being used for your complie

---

