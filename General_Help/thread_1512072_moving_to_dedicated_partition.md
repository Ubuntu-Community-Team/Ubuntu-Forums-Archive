---
title: "moving to dedicated partition"
date: 2010-06-17
forum: General Help
---

### Post by star11786 on 2010-06-17
right now i m using ubuntu 10.04 installed on virtual hard disk (wubi), but now i want to move it to dedicated hard drive partition.

i have google about this thing but the solution i found is to use LVPM however that software is NOT compatible with ubuntu 10.04. . .

Any suggestions??

---

### Post by bcbc on 2010-06-17
There is a script wubi-move-to-partition.sh referenced in the wubi guide. Like LVPM it's outdated, but you can use it to understand what's involved and do it manually, if you feel up to it. I've created a modified version of the script that works for me on 10.04, but it is like an 'alpha release' since it hasn't been tested widely and I don't recommend using it until its reviewed ([https://bugs.launchpad.net/wubi/+bug/456549](https://bugs.launchpad.net/wubi/+bug/456549))

You have to manually create the partitions first whatever method you choose.

It goes without saying, backup before doing anything.

---

### Post by star11786 on 2010-06-18
thanks for the reply but now i think i have another problem related to that first one.

currently my hard disk is 80 GB.
25 GB for C
and 
49.5 GB for D

windows is installed on C and beside that 15 GB is dedicated to ubuntu.

n the new partitions i wanna creat would be from dividing C i.e. 
7 GB for windows
1 GB swap
remaining C for ubuntu.

so i think i cant make that partition while virtual disk is on C drive (i do have a portable drive on which i can copy that virtual drive file to, but then it can't be used without modifying)

the most easiest thing i can think of is to make the backup of all the packages, delete ubuntu and install fresh copy from the USB(as my CD-ROM is not working condition) and make partition before installation, copy those packages into the cache and install them.

if u have any other EASY suggestion, then plz share it with me. . .

---

### Post by bcbc on 2010-06-18
> **star11786 said:**
> 
if u have any other EASY suggestion, then plz share it with me. . .

Not that I am aware of. You could backup a part of D:, shrink D: to make a new extended partition, move wubi to it, and then move the part of D: you backed up to the new space on C:

I wouldn't bother doing this unless there is a lot of customization of settings and user data on your wubi. If not, a reinstall from usb is the simplest.

If you do have some data on the wubi install you need, then back up the root.disk and then you can copy it over later. You could probably copy your entire /home over it.

---

