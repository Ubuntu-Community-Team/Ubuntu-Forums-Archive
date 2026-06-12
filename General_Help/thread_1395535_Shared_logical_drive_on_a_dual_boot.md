---
title: "Shared logical drive on a dual boot"
date: 2010-02-01
forum: General Help
---

### Post by kayaksmak on 2010-02-01
So, I've got a dual boot with 7 & Karmic.  Unfortunately, as I'm coming to use and like Karmic more and more, I'm running out of space on the 15Gb that I partitioned for it.  I want to make another logical partition on the windows side of the current partition to create a drive accessible by both windows.  Is there any way to do this or the filesystems for Windows and Linux incompatible? thanks!

---

### Post by garvinrick4 on 2010-02-01
First run CODE:

sudo fdisk -l         (that is small L)

Post it on this thread and there will be a lot of users that help you partition your drive.

---

### Post by kayaksmak on 2010-02-01
It's not an issue of partitioning the drive.  I can and need to do that in windows.  I was just wondering if I need to use a specific file system or something to make it available in both windows and linux.  

nonetheless
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12       17499   140471292    7  HPFS/NTFS
/dev/sda3           17500       19457    15727635    5  Extended
/dev/sda5           17500       19369    15020743+  83  Linux
/dev/sda6           19370       19457      706828+  82  Linux swap / Solaris

```

---

