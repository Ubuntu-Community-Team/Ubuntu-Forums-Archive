---
title: "Partitions not showing"
date: 2011-05-08
forum: General Help
---

### Post by oxama on 2011-05-08
there are 4 drives in my PC. now i have installed natty on it and I can't see other drives except the filesystem.

can you suggest me a tool that can make all my partitions visible.

PS: I used live CD to install Ubuntu 11.4

---

### Post by carl4926 on 2011-05-08
Please post result of

```
sudo fdisk -l
```

---

### Post by oxama on 2011-05-09
here is the screenshot of sudo fdisk -l

---

### Post by carl4926 on 2011-05-11
4 HD's?

Umm...

Are they internal SATA HD's?

That partitioning is strange too, who made it like that?

---

### Post by oxama on 2011-05-11
single HD with 4 partitions.

---

### Post by carl4926 on 2011-05-11
> **oxama said:**
> single HD with 4 partitions.

Yes
That's what I see

But you said
> there are 4 drives in my PCDoes that mean 4 HD's or 4 partitions

Show us a screen from System Monitor > File System

---

### Post by oxama on 2011-05-11
> **carl4926 said:**
> Yes
That's what I see

But you said
Does that mean 4 HD's or 4 partitions

Show us a screen from System Monitor > File System

ok. let me send it

---

### Post by zobayer1 on 2011-05-11
I just tried fdisk -l and the output is different, specially the filesystem in your screen shot is SFS (idk what the first S means actually, is it self certifying, or secure)
```


Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40a540a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4998    40143872    7  HPFS/NTFS

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4fad4fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188       20022   135226760    f  W95 Ext'd (LBA)
/dev/sdb5            3188        8286    40957686    7  HPFS/NTFS
/dev/sdb6            8287       13385    40957686    7  HPFS/NTFS
/dev/sdb7           16573       20022    27711488    7  HPFS/NTFS
/dev/sdb8           13386       13634     1998848   82  Linux swap / Solaris
/dev/sdb9           13635       16572    23598080   83  Linux

Partition table entries are not in disk order

```

I can see all my drives (partitions) clearly in "Computer"

---

### Post by srs5694 on 2011-05-11
"SFS" indicates a Windows [Logical Disk Manager (LDM)](http://en.wikipedia.org/wiki/Logical_Disk_Manager) partition, aka a "dynamic disk" structure. This is Bad News from a Linux perspective. I'm actually surprised you managed to get Ubuntu install on the disk -- or are you running from a live CD?

As a general rule, the best approach to dealing with LDM is to use a Windows tool such as [EASEUS](http://www.partition-tool.com/personal.htm) or [Partition Wizard](http://www.partitionwizard.com/) to convert from LDM to conventional ("basic" in Windows terminology) partitions. You can then use Linux partitioning tools to manipulate the partitions and get Linux installed. Note that I've never used EASEUS or Partition Wizard; I'm just mentioning them because I've heard that they can do the conversion. This is a potentially risky operation, so you should back up your important data before proceeding.

A somewhat less risky, but more expensive, option is to add a hard disk for Linux. You can then leave your current hard disk alone.

---

