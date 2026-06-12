---
title: "can't execute bash files [fsta/mtab problem?]"
date: 2011-06-04
forum: General Help
---

### Post by SkippoGuangiacomo on 2011-06-04
Hi, 

I've been trying some bash again (I did not program for a few years, since kubuntu 9.04 I think). However I run into 'security' problems (I think). For example, when I run ./hello.sh I get the following error: 
"bash: ./hello.sh: Permission denied"
The file "hello.sh" is executable, as happens after issuing the command "sudo chmod a+x hello.sh" or "sudo chmod u+x hello.sh".

I then remembered that the partition in which the file is running should also be executable. I checked the fstab partition and made it executable. The fstab file now says the disk is executable: 
"
#/dev/sda3
UUID=0207ffa3-e2f6-4194-b2ae-7989d07650a0 /mnt/BIGdisk    ext3    relatime,users,auto,rw,exec 0       0
"
but mtab says : 
"
/dev/sda3 /mnt/BIGdisk ext3 rw,nosuid,nodev,relatime 0 0
"

How can I make it executable again?
Thank you very much for your help.

p.s. the other "issue" is that if I call "bash hello.sh" the hello.sh command works perfectly. I would like to call the command only with "./hello.sh", but I am wondering if I'm just making a big fuzz of nothing?
p.p.s.s.: This is hello.sh
>#!/bin/bash
>echo "Hello World"

(without ">")

I am running kubuntu 11.04, KDE 4.6.2

---

