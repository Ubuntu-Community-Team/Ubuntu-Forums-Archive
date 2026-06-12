---
title: "Unable to mount Windows partition"
date: 2009-10-31
forum: General Help
---

### Post by LucidStrike on 2009-10-31
I can't mount my Windows partition from Kubuntu.

Here's fdisk -l:

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0ddb0dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1241     9964048+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1241       13399    97656250    7  HPFS/NTFS
/dev/sda3           13400       30401   136568565    5  Extended
/dev/sda5           13400       30031   133596508+  83  Linux
/dev/sda6           30032       30401     2971993+  82  Linux swap / SolarisI'd appreciate some assistance. :D

SAVING FACE: Not my computer, else I there wouldn't be any Windows. D:<

---

### Post by lilbill on 2009-10-31
Have you installed ntfs support? Namely,
```

sudo apt-get install ntfs-3g ntfs-config

```
After that there will be an application under System-->Administration  called ntfs configuration open that up and follow the directions.  You'll pick a mount point for the drive and allow read/write for ntfs drives.

Best!

---

### Post by LucidStrike on 2009-11-02
Thanks, but it didn't help. In fact, it didn't ask me much. Asked me if I wanted user to access internal or external space or somethin' like that. Neither of the two options presented helped. It didn't ask about partitions or mounting. :(

---

