---
title: "Tweaking LVM2 for 4K drives"
date: 2011-03-18
forum: General Help
---

### Post by aeqel on 2011-03-18
Hello,

Preface:
I have just bought two new WD20EARS hard drives and have added them into my LVM and moved all my data from my old failing seagate drives to my new drives. I also have a WD10EARS in the LVM.
These are WD Caviar Green Power 4K hard drives.
Using Ubuntu 10.10 64bit and LVM2, everything is working but I want to know if I can tweak it for more performance. I am relatively new.

Questions:
1. How can I check if the 4K drives are aligned?
2. How can I check what block size LVM is using?
3. I didn't partition one of the WD20EARS when adding it to a LV, will this be problematic or effect performance? Can I partition it without losing the data that is on it now? 
4. I heard XFS is better than EXT4 for large files and people tend to suggest using certain formats when they're talking about LV's, if I check the format of any of the hard drives it says they are lvm2...?

Cheers.

---

### Post by srs5694 on 2011-03-18
> **aeqel said:**
> Questions:
1. How can I check if the 4K drives are aligned?

The short answer is to type:

```

sudo fdisk -lu
```

That will produce a list of partitions. Examine the start sector numbers. If all of the primary and logical partitions begin on sector numbers that are multiples of 8, then you're fine. If not, then you're likely to get abysmal performance when writing small files.

The long answer is in [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for IBM developerWorks a while back.

> 2. How can I check what block size LVM is using?

The pvdisplay utility shows you the physical extents (PE) size, which is the allocation block size that LVM uses by default. It's normally 4 MiB. If you align the partition on which you create a physical volume to the 8-sector mark, everything else will be fine.

> 3. I didn't partition one of the WD20EARS when adding it to a LV, will this be problematic or effect performance? Can I partition it without losing the data that is on it now? 

"No" to both questions. On a truly unpartitioned disk, the physical volume begins on sector 0, which is properly aligned. Once you begin using the disk in an LVM in this way, though, you can't easily add partitions; you'd need to remove the disk from the volume group, partition it, re-create the physical volume data in one or more partitions on the disk, and add the new partition(s) back to the volume group. This is the main drawback to using disks "raw" in an LVM. There's also a slim chance that you'll slip up with a partitioning tool (fdisk, GParted, or whatever) and damage the LVM.

Note that all this assumes the disk is truly unpartitioned; if you just created a single big partition on the disk, it will be easier to resize that partition and add others, and the partition might or might not be properly aligned.

> 4. I heard XFS is better than EXT4 for large files and people tend to suggest using certain formats when they're talking about LV's, if I check the format of any of the hard drives it says they are lvm2...?

Whatever utility you're using is looking at partitions (or perhaps even raw disks), not the logical volumes they contain. Try this:

```

sudo blkid /dev/mapper/*

```

That will show you what's in use in your logical volumes. (Using "sudo blkid" alone, without any arguments, should show this, too, along with whatever's in use in any partitions you've got.)

As to which filesystem is best, that's an area that can provoke religious zeal. A response that's actually helpful would require that you specify what you intend to do with the disk.

---

### Post by aeqel on 2011-03-18
Thanks for your reply srs5694.

I am using the three hard drives mainly for storage and playback of high definition media however is also my home directory. So all round performance would be ideal and I'm not really interested in all the super fancy stuff I can do with LVM other than being able to add more space.

Seems like my LV is running in ext4:

```
zxc@zxc-desktop:~$ sudo blkid /dev/mapper/*
/dev/mapper/DATA-Storage: UUID="7e5e5424-c8e1-47eb-9092-1d21310bc680" TYPE="ext4" 

```

Some problems though.. it appears my PE size is 1GB!! Is this a problem? (The two smaller Seagate hard drives are also in here but aren't assigned to any logical volume so I deleted them from the output)
```
lvm> pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               DATA
  PV Size               931.51 GiB / not usable 525.71 MiB
  Allocatable           yes (but full)
  PE Size               1.00 GiB
  Total PE              931
  Free PE               0
  Allocated PE          931
  PV UUID               IdD52c-bLiU-9T9O-Jnjv-szox-ScQF-bsugP1
   
  --- Physical volume ---
  PV Name               /dev/sde1
  VG Name               DATA
  PV Size               1.82 TiB / not usable 17.09 MiB
  Allocatable           yes (but full)
  PE Size               1.00 GiB
  Total PE              1863
  Free PE               0
  Allocated PE          1863
  PV UUID               HfR0bn-UB0y-j66O-TIj0-iEJB-rvET-F670MU
   
  --- Physical volume ---
  PV Name               /dev/sdf
  VG Name               DATA
  PV Size               1.82 TiB / not usable 17.09 MiB
  Allocatable           yes (but full)
  PE Size               1.00 GiB
  Total PE              1863
  Free PE               0
  Allocated PE          1863
  PV UUID               Q742cx-dwHF-Xvt3-Jd1R-YVNb-CsJo-ewrrqH

```


And finally, looks like the two that are partitioned are starting at sector 1...

```
zxc@zxc-desktop:~$ sudo fdisk -lu
 ########## OS Installed here ##########
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009b957

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   149792767    74895360   83  Linux
/dev/sda2       149794814   156248063     3226625    5  Extended
/dev/sda5       149794816   156248063     3226624   82  Linux swap / Solaris

 ########## WD10EARS ##########
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1953525167   976762583+  8e  Linux LVM

 ########## This is one of the small hard drives that I'm replacing #########
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   976773167   488386583+  8e  Linux LVM

 ########## This is one of the small hard drives that I'm replacing #########
Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1   488397167   244198583+  8e  Linux LVM

 ########## NEW HDD's from  here ##########
Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  3907029167  1953514583+  8e  Linux LVM

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/dm-0: 5000.4 GB, 5000415674368 bytes
255 heads, 63 sectors/track, 607932 cylinders, total 9766436864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

```

---

### Post by aeqel on 2011-03-19
Hmmm another problem, the operating system only seems to pick up 2.5TB of hard drive space in my home directory anyway... 
It seems like the raw formatted hard drive simply is not being acknowledged however the LVM and Disk Utility sees it all as 5TB.

So I think I'm going to have to reduce the size of the LV to free up enough extends to move everything to one hard drive, remove two of the hard drives, format them correctly, add them back to the LV again, remove the other hard drive, format that correctly, then add it back into the LV again...

How on earth do I do that without data loss? My home directory is only just over a terrabyte..

---

### Post by aeqel on 2011-03-19
Hmmm another problem, the operating system only seems to pick up 2.5TB of hard drive space in my home directory anyway... 
It seems like the raw formatted hard drive simply is not being acknowledged however the LVM and Disk Utility sees it all as 5TB.

So I think I'm going to have to reduce the size of the LV to free up enough extends to move everything to one hard drive, remove two of the hard drives, format them correctly, add them back to the LV again, remove the other hard drive, format that correctly, then add it back into the LV again...

How on earth do I do that without data loss? My home directory is only just over a terrabyte..

---

### Post by srs5694 on 2011-03-19
It sounds like your /home logical volume hasn't yet been expanded to cover the new space available on your new drives. That could actually make recovery easier. I say "recovery" because, if your new 2 TB drives have partitions starting at sector 1, they are *not* properly aligned, so you'll need to remove them from your LVM configuration, re-partition them, and add them back.

You may want to look into a GUI tool for doing your LVM manipulations, such as kvpm or system-config-lvm. (At least one of these is in the Ubuntu repositories, IIRC.)

---

