---
title: "Drive trouble"
date: 2011-07-27
forum: General Help
---

### Post by jyrous on 2011-07-27
Hi,
My father tried to install Ubuntu alongside windows XP, but it didn't work properly. After the installation I could boot ubuntu but no option for windows. I could see the two partitions and all the windows files in a filesystem, so I tried to delete the ubuntu partition with gparted (using the liveCD, not a good idea....), and now when I boot it says "BOOTMGR" is missing, press cnt-alt-del to restart. 

I thought i could use my windows xp cd to repair the drive, but it says that it can't detect any hard drives.....

IS there any way to repair the drive using the LiveCD? 
PLease help me!
any help is much appreciated

---

### Post by jyrous on 2011-07-27
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9728    78138368    7  HPFS/NTFS
/dev/sda2   *        9729       30400   166047809+   5  Extended
/dev/sda5            9729       30400   166047808+   7  HPFS/NTFS

something wrong with the sda2 extended????

please help

---

### Post by Mark Phelps on 2011-07-27
> **jyrous said:**
> Hi,
My father tried to install Ubuntu alongside windows XP, but it didn't work properly. After the installation I could boot ubuntu but no option for windows. I could see the two partitions and all the windows files in a filesystem, so I tried to delete the ubuntu partition with gparted (using the liveCD, not a good idea....), and now when I boot it says "BOOTMGR" is missing, press cnt-alt-del to restart. 
You SURE it was XP? That error message is for Vista/Win7, not for XP.

> I thought i could use my windows xp cd to repair the drive, but it says that it can't detect any hard drives..... If it's a recent PC, it probably has SATA drives -- and the early XP CDs didn't include drivers for SATA drives, only IDE drives.

> IS there any way to repair the drive using the LiveCD? 
That depends on "repair the drive" means -- as there is probably nothing really wrong with "the drive" itself.

What I would suggest is that you boot into a LiveCD.  Once there, go the the Home icon on the left (presuming you're using 11.04 and Unity), click it, and look through the list of partitions.  If you see something that could be your XP partition, click it.  That will open Nautilus pointing to that drive.  Look through that and tell us what folders are there.

If you see a folder named boot and you see a file in there named BCD -- that is Vista/Win7, not XP.

---

