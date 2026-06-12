---
title: "Only 90+mg usable space on 750mg HD"
date: 2010-12-06
forum: General Help
---

### Post by tonypg on 2010-12-06
Hi,
 I installed Ubuntu on my new laptop which came with a trial vers on Win 7.
I am thinking that the drive has been partitioned so that Ubuntu is only allocated 90+meg. Is there anyway i can change this. As i am not using Win 7 at all.

---

### Post by shoot2kill on 2010-12-06
Im guessing you mean 90/750 GB?

can you post your output of

```
sudo fdisk -l
```

---

### Post by tonypg on 2010-12-07
Here is the fdisk -l info.

```
Disk /dev/mmcblk0: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         957     1929244+   6  FAT16

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x808876f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       89648   718556160    7  HPFS/NTFS
/dev/sda3           89648       91202    12480512   17  Hidden HPFS/NTFS

```

---

### Post by Mark Phelps on 2010-12-08
> **tonypg said:**
> Hi,
 I installed Ubuntu on my new laptop which came with a trial vers on Win 7.

Laptops don't come with "trial" versions of Windows 7!  IF yours did, then the vendor ripped you off big-time!

---

### Post by coffeecat on 2010-12-08
> **tonypg said:**
> Hi,
 I installed Ubuntu on my new laptop which came with a trial vers on Win 7.
I am thinking that the drive has been partitioned so that Ubuntu is only allocated 90+meg. Is there anyway i can change this. As i am not using Win 7 at all.

Assuming you do mean 90/750 GB, I can see no evidence of your having installed Ubuntu at all - or at least on its own dedicated partition. Your partition layout on the 750.2GB drive shows these sizes:

Partition 1 (sda1) - 1.6GB
Partition 2 (sda2) - 735.8GB
Partition 3 (sda3) - 12.8GB (hidden)

My guess is that sda1 is your Windows 7 boot partition, sda2 Windows C: and sda3 a manufacturer's restore/recovery partition. When you say you installed Ubuntu, do you mean that you used [Wubi?]("https://help.ubuntu.com/community/Wubi")

---

