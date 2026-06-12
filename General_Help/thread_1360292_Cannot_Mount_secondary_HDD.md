---
title: "Cannot Mount secondary HDD"
date: 2009-12-20
forum: General Help
---

### Post by JackRock on 2009-12-20
When attempting to open my secondary (IDE) hard drive, it says 

> Unable to mount <Name> | Authentication is requiredI try to go to the "Computer" location and "Open as Administrator", but get the following message:

> Unable to determine program to run.  The item you selected cannot be run as administrator powers, because the correct application cannot be determinedSo I tell it to open with "Open Folder", which gives the same result.  I did some searching, and another user had  similar problem, and it was suggested to run ntfsfix, which I did.  No dice.  Here are the results of the fdisk -l command:

> jackrock@JR-Desktop:/mnt$ sudo fdisk -l
[sudo] password for jackrock: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20ea3cf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59687   479435796   83  Linux
/dev/sda2           59688       60801     8948205    5  Extended
/dev/sda5           59688       60801     8948173+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03680367

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24322   195358720    7  HPFS/NTFSThe main drive is a SATA 500GB, which is what the OS is installed on.  It's working fine.  The drive I'm having a hard time getting into is a 200GB IDE drive.  It's being detected by the BIOS, but not mounted in Ubuntu.

I was running just fine yesterday, but nothing today.  Any takers?

---

### Post by JackRock on 2009-12-20
I was able to fix this problem by using [FONT=monospace]pysdm.[/FONT]

---

