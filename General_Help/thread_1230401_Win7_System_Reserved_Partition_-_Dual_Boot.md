---
title: "Win7 System Reserved Partition - Dual Boot"
date: 2009-08-03
forum: General Help
---

### Post by scrtyfrk on 2009-08-03
How do you prevent Ubuntu from mounting the System Reserved partition on a dual boot system with Windows 7?  /etc/fstab does not have any mention of that partition.

---

### Post by baddnady23 on 2010-03-03
I have the same question... Bump?

---

### Post by xouns on 2010-05-26
And more importantly, I can only have four partitions, so it's hard to have a proper dual boot, no?
1. System Reserved (Windows 7, swap files?)
2. Windows 7
3. Ubuntu
4. Ubuntu swap files
5. Data (oh noes!)

How easy is it to make a "nested" partition in Ubuntu? I had this once, but I used partition magic back than.

---

### Post by oldfred on 2010-05-26
The system reserved is the windows boot and repair partition. 

You can install Ubuntu and swap into logical partitions that are all in one extended partition. Data whether NTFS or linux partition can also be in a logical partition and windows will see an NTFS partition (but not linux partitions).

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

