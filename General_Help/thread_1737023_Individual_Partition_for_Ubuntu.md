---
title: "Individual Partition for Ubuntu"
date: 2011-04-22
forum: General Help
---

### Post by Richiegs on 2011-04-22
I initially installed Ubuntu into my PC within Windows XP. Now I want to create a separate partition for Ubuntu. I wonder if it is possible to move the Ubuntu part within Windows XP into a new partition, so this will save me a lot of time and effort.
Moreover, I am using 32-bit Ubuntu within Windows XP. I would like to know if it is possible to create a separate partition for 64 bit Ubuntu and also keep the 32 bit Ubuntu within Windows. Thank you for any advice.

---

### Post by oldfred on 2011-04-22
You end up doing a clean install, since you are changing from 32bit to 64. But you can copy your /home which has your user settings & files into a the new home. I always suggest separate /home as part of the install. Windows needs lots of free space in the NTFS partition so do not shrink it too small. About 20% freee is the smallest you should let the NTFS partition get.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you do it manually:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Richiegs on 2011-04-27
> **oldfred said:**
> You end up doing a clean install, since you are changing from 32bit to 64. But you can copy your /home which has your user settings & files into a the new home. I always suggest separate /home as part of the install. Windows needs lots of free space in the NTFS partition so do not shrink it too small. About 20% freee is the smallest you should let the NTFS partition get.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you do it manually:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Thanks. This is a easy way to create a separate Ubuntu partition from Wubi Ubuntu. It took me about 15 minutes to complete. If not, I would have to spend the whole day to install Ubuntu. Thanks again!

---

