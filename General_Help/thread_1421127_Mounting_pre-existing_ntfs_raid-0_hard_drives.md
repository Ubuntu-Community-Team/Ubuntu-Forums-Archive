---
title: "Mounting pre-existing ntfs raid-0 hard drives"
date: 2010-03-03
forum: General Help
---

### Post by zzzPOOHzzz on 2010-03-03
I overwrote my whole windows 7 installation to switch back to ubuntu because i missed it so much... i have 4 hard drives
2x 74gb raptors (no raid)
and 2x 640gb caviar blacks (raid-0)
i have lots of data on my caviars
and now i don't know how to mount them

heres my output for fdisk -l

```

pooh@pooh-desktop:~$ sudo fdisk -l
[sudo] password for pooh: 

Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00087dca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8665    69601581   83  Linux
/dev/sda2            8666        9039     3004155    5  Extended
/dev/sda5            8666        9039     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 640.1 GB, 640135028736 bytes
256 heads, 63 sectors/track, 77521 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      266306  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 640.1 GB, 640135028736 bytes
256 heads, 63 sectors/track, 77521 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      266306  2147483647+  ee  GPT
pooh@pooh-desktop:~$ 

```

they are the sdc and sdd drives that should be together as one, and they are ntfs

---

### Post by psusi on 2010-03-03
This looks like it was a Windows software raid, not a hardware fake raid.  If so, then you can't access them from Linux AFAIK.

---

### Post by zzzPOOHzzz on 2010-03-03
> **psusi said:**
> This looks like it was a Windows software raid, not a hardware fake raid.  If so, then you can't access them from Linux AFAIK.

ahhh crap... youre probably right. i did do it from within windows... oh well... thanks!

---

