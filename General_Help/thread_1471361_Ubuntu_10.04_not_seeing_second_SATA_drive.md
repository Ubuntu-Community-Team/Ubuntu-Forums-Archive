---
title: "Ubuntu 10.04 not seeing second SATA drive"
date: 2010-05-03
forum: General Help
---

### Post by thered on 2010-05-03
I was running a dual boot, xp and ubuntu on my desktop. I decided to go all Linux with the new distro.

My unit has 2 x 200gig SATA drives - ubuntu and xp shared one and the other was partition into two -both NTFS for data storage.

I used Gparted to wipe the first drive and tried to install Ubuntu - it wouldn't format saying the disc was in use, which was strange.  A trip into BIOS found that I had RAID enabled - I disabled this function and Lucid install and started up OK. Installed Gimp and some other stuff, tweaked Firefox.

Started Nautilus File Manager and to my surprise it failed to find (see) the other SATA drive.

If I run Sys>>Admin>>Disc Utility it sees the other drive and the partitions. It won't let me format it or delete the partition though.

There are files on the other drive, but I have them backed up, so not bothered if I have to wipe it.

Just wondered why I can't access or see the other drive -at present I only have access to half my storage.

Any Ideas?

Russ

---

### Post by thered on 2010-05-03
Eventually sorted it.

The drive was still marked as part of RAID (although never setup as such)

Zapped partitions with Gparted on Live CD and formatted to ntfs.

Now ok :D

---

