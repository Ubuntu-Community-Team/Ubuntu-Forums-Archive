---
title: "patitioning ubuntu in ubuntu 10.04.4LTS"
date: 2012-08-20
forum: General Help
---

### Post by mk631219 on 2012-08-20
to everybody.
right now i am writing this to you on a trial download version of ubuntu 10.04.4LTS on a pc that i built and i want to know how i can put a root partition along side of my copy of windows xp professional on the same hard drive on different places such as c:/ and x:/ as the root partition because I want to be able to duel boot them, but i do not have the disk to partition the hard drive for a root partition. could you help me out so that i can run both of them on this hard drive. :???:

---

### Post by oldfred on 2012-08-21
You can only have 4 primary partitions, but you can make one primary an extended partition to hold many logical partitions. You can use gparted from the Ubuntu liveCD, but I might download the gparted liveCD so you have to most up-to-date version.

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

