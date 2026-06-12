---
title: "MBR Corrupted --- Please Help !!!!"
date: 2011-03-28
forum: General Help
---

### Post by Jack3500 on 2011-03-28
I have a 1TB hard drive with about 6 partitions on it.  Including NTFS, EXT4, and HFS+ partitions. I loaded a backup image file  for one of the operating systems and this ended up slightly messing up  the MBR. I usually fix this by using a small MBR writing program.  However this time instead of fixing the MBR, it corrupted it.  

Now any partition or recovery software that i use says that its  unable to read from the drive or says that its unallocated, but Im sure  theres a way to get the data back by simply fixing the partition tables 

however i have never done this before and so far all the partition  programs i used didnt work  
any help would be very appreciated

---

### Post by srs5694 on 2011-03-29
First, please post the output of the following command:

```

sudo fdisk -lu

```

Note that's a lowercase "L", not a digit "1", in "-lu". Please post the results between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

Second, disks with HFS+ partitions often use the GUID Partition Table (GPT) partitioning system rather than the more common Master Boot Record (MBR) partitioning system. This is particularly likely to be true on Intel-based Macintoshes, although it might not be true on external disks you use on both commodity PCs and Macs. If your disk uses (or used to use) GPT, then editing the MBR might be useless or even damaging. Thus, it's critical that you know which partitioning system your disk uses. Fortunately, fdisk is smart enough to look for GPT data and warn about its presence, although fdisk doesn't work with GPT data structures. OTOH, it's conceivable that whatever you did has damaged or destroyed the GPT data structures, in which case it might be imperative that you know which partitioning system your disk uses. Thus, any information you can give about this would be helpful. How was the disk originally partitioned? (Using GParted, a Windows partitioner, a MacOS partitioner, etc.?) Was OS X ever installed on the disk? If you know for certain that the disk does or does not use GPT, please say so. If the disk used to use GPT but has now been converted to use MBR only, that's also critical information, since old and irrelevant GPT data structures might remain behind on the disk, and you don't want to restore them in such a situation.

---

