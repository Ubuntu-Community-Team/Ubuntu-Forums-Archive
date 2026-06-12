---
title: "Reload partition table after creating a partition"
date: 2009-09-27
forum: General Help
---

### Post by GrayBear on 2009-09-27
I create a new partition with cfdisk (or with fdisk) - /dev/hda5, but after that, I try a format:
```
mke2fs /dev/hda5
```and i get 
```
"Could not stat /dev/hda5 --- no such file or directory"
The device apparently does not exist; did you specify it correctly?
```how can I convince mke2fs to see the /dev/hda5 partition without a restart?

thanks

---

### Post by lloyd_b on 2009-09-28
> **GrayBear said:**
> I create a new partition with cfdisk (or with fdisk) - /dev/hda5, but after that, I try a format:
```
mke2fs /dev/hda5
```and i get 
```
"Could not stat /dev/hda5 --- no such file or directory"
The device apparently does not exist; did you specify it correctly?
```how can I convince mke2fs to see the /dev/hda5 partition without a restart?

thanks

Try "sudo partprobe".  This utility refreshes Linux's partition table.

Note: If that program isn't found, "sudo apt-get install parted" (it's part of the parted partition editor package).

Lloyd B.

---

