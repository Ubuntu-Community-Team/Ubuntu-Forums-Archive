---
title: "what repo do get retro packages namely gdk 1.2"
date: 2012-08-16
forum: General Help
---

### Post by gcomputersci4 on 2012-08-16
I have ubuntu 12.04 lts. the game Privateer requires the retro package libgdk1.2 to install where do i get it.

---

### Post by gcomputersci4 on 2012-08-24
This is what I get when i try to install the gdk 1.2 on ubuntu 12.04 LTS .
```
sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgtk1.2
E: Couldn't find any package by regex 'libgtk1.2'
```
 I need that old package.  What repository is it located in. I would like to add only one line  to my "sources.list"  file. Thank-you

---

### Post by sandyd on 2012-08-24
> **gcomputersci4 said:**
> This is what I get when i try to install the gdk 1.2 on ubuntu 12.04 LTS .
sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgtk1.2
E: Couldn't find any package by regex 'libgtk1.2'
 I need that old package.  What repository is it located in. I would like to add only one line  to my "sources.list"  file. Thank-you
The last time that package shows up is in hardy

You will have to ask the program/game 's creator to send out an update, or attempt to compile the game yourself.

---

