---
title: "Partation not found"
date: 2011-09-11
forum: General Help
---

### Post by tameemalauddin on 2011-09-11
I'm quite new to Ubuntu 11.04 and Ubuntu. while I was installing, I went to the partition menu to partition the disk.
so this is what i did,
-1024Mb to /boot(ext4)
-2048 to swap
-10240 to / (ext4)
-315000 to /home (ext4)
-and the rest to /usr (ext3)

NOW HOW DO I CREATE 2 DRIVES IN UBUNTU LIKE WINDOWS (: C) AND (: D)?

AND I AM UNABLE TO FIND THE /usr(ext3) partition. How do I understand this?
How should I find this?

---

### Post by jv2112 on 2011-09-12
Linux mounts all drives in one file-system under a directory tree. The use of letters as in Windows does not exist. All drives appear in the file-system tree and don't appear any different. However if you want separate partitions to organize your data just segment another partition. 


However, if you are new I would suggest using folders to segment out the data as it would be simpler. 


_______________________________________
/dev/sda1


sdX [ A -Z ] -- Letter is the physical drive connected to the controller on your motherboard. 1st controller = A , 2nd controller = B & so on.


sdaX [ 0 - 9 ] -- The number is your partition on the drive. 

mount point -- > Like / (beginning of tree ) is where it is mounted (accessed ) 


File - System definitions: Open up a terminal and enter->

man hier ( You will understand where your usr went after reading) 


This will help you understand partitioning better - 

[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

____________________________________________

---

### Post by Topsiho on 2011-09-12
> **tameemalauddin said:**
> I'm quite new to Ubuntu 11.04 and Ubuntu. while I was installing, I went to the partition menu to partition the disk.
so this is what i did,
-1024Mb to /boot(ext4)
-2048 to swap
-10240 to / (ext4)
-315000 to /home (ext4)
-and the rest to /usr (ext3)

NOW HOW DO I CREATE 2 DRIVES IN UBUNTU LIKE WINDOWS (: C) AND (: D)?

AND I AM UNABLE TO FIND THE /usr(ext3) partition. How do I understand this?
How should I find this?


Apart from what reason you may have for creating an /usr partition (your personal files and everything will be placed in the /home partition), you have tried to create 5 partitions on a disk, and that is not possible: 4 PRIMARY partitions is the maximum possible number (in any Operating System, it's a disk feature)
A separate /boot partition is not necessary too. It used to be when certain boot files (I forgot which, but they were in /boot) had to be in the lower cylinders (in the beginning) of the disk, so one made this certain with a separate /boot, in the beginning of the disk.

So that is getting rid of one of your primary partitions.

The best thing to do, just to be prepared for later is:

Create 1 PRIMARY partition: /sda1, for the root partition: /, ext4, about 10 or 15 GB (5 is enough, but with 15 you will not get stuck so soon :). / will contain all the ***system*** files.
Create a number of LOGICAL partitions, these come (automatically) in a container, which is called sda2, if you follow yhis advise. sda2 is a PRIMARY partition too.

The LOGICAL partitions are for:

the /home partition. ext4, as large as possible, see however the space you need for swap, in the next partition you'll have to create.
/home will contain ALL PERSONAL files and settings and so on. The files you'll want to keep when you re-install later.

a swap partition: twice your RAM (working memory of the computer). You used 2 GB, which is OK when the RAM is 1 GB.

The Logical partitions are called (automatically) /sda5, sda6, etc.

And as already said by jv2112: C: and D: is Windows talk, and in Linux we speak ... Linux :). Linux has just one filesystem, hanging under one root directory /, even when this filesytem is distributed over any number of drives. This is one reason that Linux is easy to use and understand, compared to another well known Operating System :)

Topsiho

---

