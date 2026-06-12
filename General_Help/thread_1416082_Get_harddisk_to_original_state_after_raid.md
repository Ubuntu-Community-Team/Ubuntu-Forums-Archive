---
title: "Get harddisk to original state after raid"
date: 2010-02-25
forum: General Help
---

### Post by tomchen516 on 2010-02-25
i am currently trying to do software raid 1 on a running ubuntu 9.10 system with mdadm. I might have done something wrong and im trying to go back from the beginning. Does anyone know how to remove all the raid info from a harddisk and get it back to its original state. Thanks!

---

### Post by dabl on 2010-02-25
Depends on what you mean by "original" ...

If you want to zeroize the drive's partition table, so it is ready to be partitioned (i.e. like a new OEM drive), then you can use "dd".

With the drive connected to your running Linux system, use ```
sudo fdisk -lu
``` to determine the /dev/sd*x* number of the target drive.

**NOTE:  You do NOT want to be wrong about this!**

Then when you're sure, you can issue

> sudo dd if=/dev/zero of=/dev/sd*x* bs=512 count=1

where "x" is the letter than you learned from fdisk.

Then run GParted, choose "MS-DOS" as the partition table type, and proceed with partitioning.

---

### Post by tomchen516 on 2010-02-26
thank you that's what i needed

---

