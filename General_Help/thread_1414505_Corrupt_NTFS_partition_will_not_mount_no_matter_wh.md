---
title: "Corrupt NTFS partition will not mount no matter what"
date: 2010-02-23
forum: General Help
---

### Post by spencer.dupre on 2010-02-23
The machine in question came with Vista on one giant 500 GB partition, and I can't get rid of Vista because my family is used to it, although my younger brothers like Ubuntu better. :D

I installed Jaunty on it within a week of getting it, then upgraded to Karmic, all was well.  Then one day the Windows NTFS partition would no longer mount.  It gave me a message about running chkdsk /f and reboot Windows twice; this I have done numerous times now to no effect.

I recently wanted to fix some issues in the way I had set up Ubuntu, so I backed up and deleted it's partitions.  This removed GRUB, and thus Windows no longer booted.  I fixed this by running Bootrec off a Vista Repair CD I got off bitorrent.  Windows was back good as new.

Now I want to put back on Ubuntu, but it doesn't detect Vista for a proper dual boot.  It recognizes the NTFS partition as NTFS, but gparted won't resize or move it; it yields the same error as when I try to mount it.  I have tried Testdisk, I have tried chkdsk run from the Vista Repair CD and I have rebooted the thing properly many times.

Any ideas?  a friend suggested Microsoft may have messed with the format to deliberately sabotage linux...

---

### Post by Mark Phelps on 2010-02-24
> **spencer.dupre said:**
>  ... Any ideas?  a friend suggested Microsoft may have messed with the format to deliberately sabotage linux...

Let me get this straight: Ubuntu not being able to recognize MS Windows stuff is somehow related to "deliberate sabotage" on the part of MS WIndows?

Also, since you claim you can run Vista OK now, how does this make the NTFS partition "corrupted"?

Presuming you can still boot into Vista, use the Disk Management utility to shrink the OS partition.  Trying to use the Ubuntu installer, or GParted, runs the risk of corrupting the Vista OS partition and rendering it unbootable.

---

