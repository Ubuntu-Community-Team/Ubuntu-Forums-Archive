---
title: "Low level format for thumb drive?"
date: 2010-12-04
forum: General Help
---

### Post by jimbob on 2010-12-04
I have a thumb drive that I cannot get a clean format done to use it as a boot device.  Running an fdisk -l gives the following:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         743     2068480    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 60, 9)
Partition 1 has different physical/logical endings:
     phys=(257, 163, 34) logical=(742, 47, 18)

Is there some way to do a lower level format (I am using Gparted) to get rid of this error?

---

### Post by AlphaLexman on 2010-12-04
Here are some ideas:
[LIST]
[*]fdformat - will do a lowlevel format for floppies (don't know if it will for a thumb drive, but I think it should.)
[*]mkfs - is a method to format a partition to put a linux filesystem on it.
[/LIST]

---

### Post by QLee on 2010-12-04
[QUOTE=jimbob]... (I am using Gparted) ...[/QUOTE]

Since you are already in gparted, have you tried deleting partition and creating a new partition with a Linux filesystem type?

---

### Post by karthick87 on 2010-12-04
Yes as @Qlee's suggestion just format the partition and create a new one.

---

### Post by uRock on 2010-12-04
Does the drive have U3 or similar software on it? If so, then you may need to go to their site and find how to remove the software.

---

### Post by jimbob on 2010-12-04
Neither fdformat nor mkfs make any difference.  Also, I have tried making a Linux ext2 fs and here is the result:

      Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         743     2068480   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 60, 9)
Partition 1 has different physical/logical endings:
     phys=(257, 163, 34) logical=(742, 47, 18)

There should be absolutely no software on the disk because earlier in the day after I couldn't do anything with it I ran dd if=/dev/zero of=/dev/sdb1 bs=512b and it cleaned off all 2Gb.

I never heard of U3 but will research it.  Thanks to all.

---

### Post by jimbob on 2010-12-05
I was finally able to clear the physical/logical discrepancies using various commands in fdisk (deleting, reformatting, etc).

My problem now is that the dongle itself is not recognized by the bios on one of my older desktop computers.  It works great with an ASUS mobo but the older one, a Gigabyte K8NS series, doesn't see it.  It is made by a company called CHIPSBNK which I have been unable to find a lot of info on.

The strange thing is that when it is plugged in to an already running OS it is recognized and can be read and written to just fine.  Go figure.

---

