---
title: "is it safe to delete system reserved partition?"
date: 2010-11-08
forum: General Help
---

### Post by dagame on 2010-11-08
i'm running out of partitions, i was thinking if i could get rid of the windows system reserved partition without messing any of my windows 7 OS & the recovering partition. I'm currently using grub2 to boot ubuntu & win 7.

---

### Post by dino99 on 2010-11-08
i think that w7 will not appreciate that :(

use gparted to resize the partitions or make room with bleachbit (into synaptic)

---

### Post by 3Miro on 2010-11-08
A recovery partition will probably not matter if you delete it. A system reserved (i.e. the 100MB or so that Windows 7 takes) you should never delete (unless you want to get rid of windows 7 anyway).

---

### Post by Mark Phelps on 2010-11-08
If you go to the NeoSmart Techology forums, download and install their EasyBCD program (in Win7), then run that in Win7 ...

It provides an option to migrate your Win7 boot loader files from the Reserved partition into your Win7 partition.  After that, you won't actually need the Reserved partition anymore.

---

### Post by srs5694 on 2010-11-08
I recommend you post the output of "sudo fdisk -lu" (between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility) and a description of what you want to do. There may be a way to accomplish your goal by moving and resizing, rather than deleting, partitions.

---

### Post by dagame on 2010-11-08
Thanks for responding everyone. What i am trying to do is to create a partiton only for storage, one that i could see in both ubuntu & win 7. I resized my win 7 partition from 300gb to 100gb, i want to use those 300gb to make it a storage parition, but is not letting me because i couldn't exceed the limit of 4 partitions, so i need to get rid of one of them. I am going to try mark's advice installing EasyBCD on win7, see if that get's rid of the system reserved partition.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e39a79c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    29362175    14680064   27  Unknown
/dev/sda2   *    29362176    29566975      102400    7  HPFS/NTFS
/dev/sda3       643965525   852045821   104040148+   7  HPFS/NTFS
/dev/sda4       852045822   976771071    62362625    f  W95 Ext'd (LBA)
/dev/sda5       852045824   868427775     8190976   82  Linux swap / Solaris
/dev/sda6       868429824   976771071    54170624   83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 926 cylinders, total 14651280 sectors
Units = sectors of 1 * 2048 = 2048 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       48194       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(3, 12, 21)
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/sdb2           48195    14651278    29206168    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(3, 12, 22)
Partition 2 has different physical/logical endings:
     phys=(911, 254, 62) logical=(926, 180, 59)
Partition 2 does not start on physical sector boundary.
```

---

### Post by srs5694 on 2010-11-09
The simplest solution is to move /dev/sda3 earlier on the disk, resize /dev/sda4 (the extended partition) so that it fills the available free space, and then create a new logical partition in the free space that's now part of /dev/sda4. This may take some time, depending on how much data you've got on /dev/sda3, and there's a risk that you'll end up damaging the disk (partition resize and move operations are always inherently risky). You can do all of this via point-and-click interfaces in GParted.

Another approach is to convert /dev/sda3 into a logical partition, resize /dev/sda4 to occupy the free space, and create a new logical partition where the free space resides. This will be quicker, but it requires more knowledge and/or use of unusual tools. (I don't know of anything offhand that's designed explicitly to convert primary partitions into logical partitions, but I know of at least two ways to do this with general-purpose tools. Specifically, you can use sfdisk to save partition data to a text file, then edit it, then write the changes back out; or you can use GPT fdisk (gdisk) to load the partition table and convert it (in memory) to GPT form and then export it back as MBR, converting /dev/sda3's status in the process.) There's less data movement involved in this option, which should make it safer; but if you don't know what you're doing you could end up creating invalid partitions, which would make it more dangerous. Thus, this option's safety factor vs. the previous one depends on you.

You should not attempt either of these things if /dev/sda3 is a Windows boot partition. Either should be OK if /dev/sda3 is a data partition, with the caveats about data loss.

---

