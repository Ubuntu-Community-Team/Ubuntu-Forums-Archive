---
title: "Downloading emulators"
date: 2009-11-10
forum: General Help
---

### Post by ZereoX on 2009-11-10
I just installed Ubuntu 9.10 on my Dell Latitude D800 and so I wanted to download Zsnes. I google how to do so and I get [this]("http://ubuntuforums.org/showthread.php?t=1307844"). What exactly is:

sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu2_i386.deb

zsnes -ad sdl

How am I supposed to use these commands to download Zsnes?

Sorry for the noob question.

---

### Post by jerrrys on 2009-11-10
what your doing is making (forcing) 9.10 to install a 9.04 package.  so if you want to do this open a terminal (under accessories) and enter 

sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu2_i386.deb

and then when you want to run it, open a terminal once again and enter

zsnes -ad sdl

---

