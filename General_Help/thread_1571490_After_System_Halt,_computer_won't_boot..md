---
title: "After System Halt, computer won't boot."
date: 2010-09-09
forum: General Help
---

### Post by josephshanak on 2010-09-09
This isn't completely ubuntu related,  but I'm using this forum because I'm using ubuntu to fix my problem.

Yesterday I was working on my laptop using the windows 7 partition. At some point it froze and I ended up just having to shutting it down by holding in the power button. When I started it up, it said something along the lines of "can't find bootable partition". 

So I made myself a ubuntu flash-drive, and ran ```
sudo fdisk -l
```. This is my output.

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74836e35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       30538   245088256    7  HPFS/NTFS
/dev/sda3           30539       60801   243087547+   5  Extended
/dev/sda5           30539       30787     2000061   82  Linux swap / Solaris
/dev/sda6           30788       60801   241087423+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf38e19c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS

```/dev/sda1 is my boot partition with grub2. grub2 doesn't load when the computer starts. on gParted it shows 1 mB of unallocated space before it.

/dev/sda2 is my windows 7 partition and it seems to be the one with the problem. On gParted it shows up as having an error too. After sda2 there is about 3 1/2 mBs of unallocated space.

/dev/sda3 is my linux partition. It seems fine.

Is there a way to fix it so it boots and save my Windows 7 partition, or atleast fix the boot partition so I can boot into linux?

---

### Post by Mark Phelps on 2010-09-09
> **josephshanak said:**
> This isn't completely ubuntu related,  but I'm using this forum because I'm using ubuntu to fix my problem.

If you seriously corrupted Win7, you won't be able to use Ubuntu to fix it.

When you were in Win7, did you take the trouble to use the Backup feature to create an burn a Win7 Repair CD?  Probably not ...

In that case, download and burn a Win7 Repair CD from the appropriate links below:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Once you have that CD, boot into it and run Startup Repair three times.  That should get you back up and running with Win7.

---

