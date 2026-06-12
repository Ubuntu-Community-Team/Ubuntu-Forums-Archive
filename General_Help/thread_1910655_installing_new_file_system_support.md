---
title: "installing new file system support"
date: 2012-01-17
forum: General Help
---

### Post by Synoc on 2012-01-17
I tried to install apple HFS support for my 10.10 computer. installed it with "sudp apt-get install hfsplus" and a sudo 'apt-get install hfsutils" when I did a 'cat /proc/filesystems | grep hfs" it showsd both hfs and hfsplus in there. now however after a resart they are not listed, but still installed. what did I forget?

---

### Post by imachavel on 2012-01-17
ok I just installed that stuff myself. You are using macbook with ubuntu installed instead of mac? or dual boot mac and linux? I know almost nothing about hfs mac file system, drivers, kernel, firmware, nada. Mac used to have proprietary hardware but now it's all intel based except that according to them it's not 'pc hardware' :roll eyes:

so just out of curiosity obviously I'm not the person meant to answer your thread, but what mac book are you using, and why do you need this stuff:

sudo apt-get install hfplus
[sudo] password for *****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package hfplus
*****@*****-Dimension-4700:~$ sudo apt-get install hfsutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  hfsutils-tcltk
The following NEW packages will be installed:
  hfsutils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 77.9 kB of archives.
After this operation, 238 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main hfsutils i386 3.2.6-11build3 [77.9 kB]
Fetched 77.9 kB in 1s (62.2 kB/s)   
Selecting previously deselected package hfsutils.
(Reading database ... 243310 files and directories currently installed.)
Unpacking hfsutils (from .../hfsutils_3.2.6-11build3_i386.deb) ...
Processing triggers for man-db ...
Setting up hfsutils (3.2.6-11build3) ...


installed?? :popcorn:

---

### Post by Synoc on 2012-01-18
I am using an Asus laptop dual booted Windows and Ubuntu. I have information on a Mac formated External Hard drive. I didn't format it, someone else did, I dont know why. I can't get it to read the drive, and HFS and HFSplus are no longer in my /proc/filesystems list. Not since reboot. and it didn't read them to begin with. gave an error message wrong fs type, bad superblock... etc. it IS possible the drive jsut went belly up for no good reason. the question is why doesn't the FS type show up in the list. deal with that problem first before moving on to figure out why the PC wont read the disk.

---

### Post by Synoc on 2012-01-23
bump

---

