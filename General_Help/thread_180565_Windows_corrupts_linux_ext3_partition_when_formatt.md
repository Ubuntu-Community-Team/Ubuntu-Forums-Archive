---
title: "Windows corrupts linux ext3 partition when formatting other FAT32 partition"
date: 2006-05-22
forum: General Help
---

### Post by ifokkema on 2006-05-22
Dear all,

Probably not Ubuntu specific, but have never had this until I switched and I can't find any help on the net.

I have a 250 Gb hard drive used for Linux (primary) and Windows 2000 (just gaming, really). I wanted a separate FAT32 partition to share data between Linux/Windows. Here's my partition list:

```
Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2432    19535008+  83  Linux
/dev/hda2            2433       14590    97659135   83  Linux
/dev/hda3   *       14591       16708    17012835    c  W95 FAT32 (LBA)
/dev/hda4           16709       30515   110904727+   5  Extended
/dev/hda5           16709       20102    27262273+   c  W95 FAT32 (LBA)
/dev/hda6           20103       30000    79505653+  83  Linux
/dev/hda7           30001       30515     4136706   82  Linux swap / Solaris
```

I made sure the FAT32 partitions aren't too big, 'cause I know the will not be working above a certain size.
The 17 Gb hda3 partition works fine; can read/write from both Linux and Windows. But I can't get the 26 Gb hda5 partition to work. If I format it under Linux, I can put files there but Windows doesn't see them and wants to format the partition. When I do that, put a file on there and reboot... the hda1 partition is corrupt (grub error 17, hda1 can't be mounted, superblock corrupt) and I can't boot my PC anymore. After booting with the Live CD, fsck'ing hda1 and fixing all error's, the whole lot is in lost+found. I managed to recover my system from there, but the FAT32 hda5 STILL doesn't work! It mounts OK but there is no file. fsck'ing it tells me it has reclaimed an unused cluster.

My questions:
- Why oh why does Windows touch my precious hda1 partition when formatting hda5? Uhm... maybe I need to ask Bill ](*,) 
- Why does hda3 (also FAT32) just work but not hda5?
- Anyone knows if this has to do with the fact the hda5 is an extended partition?

Thanks in advance for any help in the matter.

Ivo

---

### Post by Phlosten on 2006-05-23
> Why oh why does Windows touch my precious hda1 partition when formatting hda5

I had a similar issue when I dual booted into Win2000 one day. It did a diskcheck at start up and promptly stuffed my ext3 partition. I have no idea what it does but it sucks.

---

### Post by ifokkema on 2006-06-06
Hi guys,

This whole problem has lingered on my drive for a while now. I just found out that the Windows 2000 install CD for some reason, cannot see past the first 131 GB of the HD. Creating a partition before the 131 GB border and sticking to this partition, makes Windows work and stop messing with my other partitions (so far).

---

