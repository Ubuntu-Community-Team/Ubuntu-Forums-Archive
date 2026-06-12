---
title: "recover partition table"
date: 2009-09-10
forum: General Help
---

### Post by htroyo on 2009-09-10
hello, i had a problem with windows xp and i had to reinstall it, when i tried to recover the grub menu i were not able because there was a problem with the file stage1, then i realized that the partition table was corrupt, i tried this solution
[http://ubuntuforums.org/showthread.php?t=1147450](http://ubuntuforums.org/showthread.php?t=1147450)
but using my partition table given by:
```
sudo sfdisk -d
```
and it didn't work,
please i need help to recover the partition table to reinstall GRUB (or ubuntu)
all data is ok, i can access all partitions but cannot install ubuntu (if i attempt to install ubuntu it won't recognize my partitions, so i'll have to format all the disk and i can't backup the disk)

---

### Post by rbc on 2009-09-10
How about testdisk? 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery)
Boot the Ubuntu Live CD, then start terminal:
sudo apt-get install testdisk
Here's a tutorial:
[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

---

### Post by htroyo on 2009-09-11
> **rbc said:**
> How about testdisk? 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery)
Boot the Ubuntu Live CD, then start terminal:
sudo apt-get install testdisk
Here's a tutorial:
[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

hello, i'm not able to access my installation, but i tried to use it in the live cd, and it didn't work, it didn't recognize my hard drive

---

### Post by htroyo on 2009-09-18
any suggestion please???
a rescue utility or something like that?

---

### Post by csi_guy on 2009-09-19
you can try using a backtrack 4 beta or pre-final disk as a live distro

---

### Post by Don1500 on 2009-09-19
or you could try:

[http://partedmagic.com/index.php?option=com_content&view=article&id=89:parted-magic-32&catid=3:newsflash&Itemid=1](http://partedmagic.com/index.php?option=com_content&view=article&id=89:parted-magic-32&catid=3:newsflash&Itemid=1)

Download the ISO in windows, create the live disk, and there should be enough tools to help you.

---

### Post by htroyo on 2009-09-19
i'll try it... thanks

---

### Post by Megrimn on 2009-09-19
> **htroyo said:**
> i'll try it... thanks

lemme know if it works, I'm having the same issue...

---

