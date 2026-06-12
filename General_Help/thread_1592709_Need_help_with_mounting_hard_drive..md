---
title: "Need help with mounting hard drive."
date: 2010-10-10
forum: General Help
---

### Post by megamark on 2010-10-10
Okay, I think this should be an easy fix, I have an internal fat32 formatted drive that worked fine until some one was stupid enough to delete the files that were on there for my ubuntu to recognise it. Now it will not show up at all, and my boot off my other drive is reeeeaaaallll slow. 

Are these problems related or did i just really screw up?

---

### Post by dborba on 2010-10-10
What do you mean by files that were on there for ubuntu to recognize it?

Can you show us the output for 'sudo fdisk -l' ?

---

### Post by megamark on 2010-10-10
here is the result from sudo fdisk -l 
-------------
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29643   238107366   83  Linux
/dev/sda2           29644       30394     6032407+   5  Extended
/dev/sda5           29644       30394     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)
----------------
The drive I had missing was a 500gb. internal. Those are my other 2. 

The files that I believe caused the problem were hidden on the drive. I could be wrong.

---

### Post by dborba on 2010-10-10
AFAIK there are no files that the system depends on to see or mount the drive.

Sorry if this is redundant, but the actual drive you want is not sdb & is not even listed on 'fdisk -l' at all?

PS: I'm off for the night. If you're in a hurry you can always try asking in #ubuntu on irc.ubuntu.com:8001

---

