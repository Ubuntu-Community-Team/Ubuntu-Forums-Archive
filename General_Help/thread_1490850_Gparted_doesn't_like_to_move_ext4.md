---
title: "Gparted doesn't like to move ext4?"
date: 2010-05-22
forum: General Help
---

### Post by 133794m3r on 2010-05-22
Ok my current issue is that my ubuntu partition(my currently most used os) at the moment is getting low onspace so i decided to take 40GB from my windows one since it wasn't using it. I made it smaller and left the area unallocated. I got into gparted using the live disk and it refuses to work for me. I cannot move my ext4 partition to the 40GB partition and put that free space at the end. This is the first time i've ever had this problem. This is the first time i've ever tried ext4.

---

### Post by drs305 on 2010-05-22
It appears from your profile you've been around linux for a while. 

You might check Gparted's View, File System Support. I've not had problems using Gparted with ext4.

Of course, even with the LiveCD swap has to be unmounted before you can perform operations on the partitions. The second half of this link [Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270") covers some of the things necessary for resizing this partition - just in case you might have missed something.

---

### Post by wilee-nilee on 2010-05-22
You have to turn swap off.

---

### Post by 133794m3r on 2010-05-23
i don't use swap ever since i've moved up to 4GB of ram i keep swap off since it was never being used in the first place i didn't see a reason to give up disk space for it. I've done the same thing in windows when i did use it. Swap's off, and the only other thing was that gparted did not want to let me resize my NTFS filesystem it kept telling me that it was unable to check the file system type. Yet i could boot into it just fine, did a disk check and it revealed nothing.

And i think it's something to do with how windows shrunk it's size. Because if i recall correctly that parition the unallocated space one is in the nonextended one. If i was more awake i'd go check it once more to be sure. But the live-cd doesn't exactly boot very quickly and i'm about to head to bed since i just wanted to check this thread before i went off towards it.

here's the fdisk-l listing. And i'll post a screenshot of the image in a little while after i awake.
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x608587a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       22596   181394432    7  HPFS/NTFS
/dev/sda3           27818       38914    89128961    5  Extended
/dev/sda4           22597       27817    41937682+  83  Linux
/dev/sda5           27818       38914    89128960   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfedad30f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               3      484519   244196352    7  HPFS/NTFS

```

---

