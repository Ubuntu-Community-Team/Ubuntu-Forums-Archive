---
title: "Dual-boot common data"
date: 2012-01-18
forum: General Help
---

### Post by kevin.strijbos on 2012-01-18
Hello,

I'm fairly new to Linux, so be gentle please.

I currently got a linux dualboot installed (GRUB, with windows 7).
My linux version is 11.04, now I'd like to check if it's possible to see data that's stored in Linux in Windows. For example: if I got music in my music map in Linux, is it possible to also use the music in that music map in Windows?

---

### Post by mcduck on 2012-01-18
Sadly for you, Microsoft only supports their own filesystems (FAT and NTFS) so Windows lacks the capability to read Linux filesystems.

Tehre are some third-party drivers available, but the last time I used them they were all more or less work-in-progress, and while quite OK to read data from a Linux partition, writing data was unreliable. IF you want, you can of course try yourself in case the programs have improved lately.

Anyway, the common way to share data between the two operating systems is to have a separate shared partition, using a filesystem which both operating systems can read. And remember also that Linux has no problems reading or writing to Windows filesystems (even though you can't use one as your root partition or home directory, as they lack support for file ownerhips and permissions as LInux/Unix systems use them)

---

### Post by Mark Phelps on 2012-01-18
mcduck is correct in that writing across filesystems tends to cause problems.  And, it can be something a simple as using one OS to update a playlist in a filesystem owned by the other OS.

BEST way to share data was also mentioned -- separate shared data partition.

Since you're running Win7, if you want to shrink the Win7 OS to make room to create a shared NTFS data partition, use the builtin Disk Management utility to do that.  Don't try to shrink it from Ubuntu or use Linux utilities to do that.

Once the Win7 OS partition has been shrunk, you can use the same utility to create a new NTFS partition -- but BEFORE you do this, look at the partitions in the Win7 Disk Management utility and confirm that you don't already have 4 primary partitions (or three Primary and an Extended).  If you do, and you force the creation of ANOTHER partition, Win7 will automatically convert your Windows partitions to Dynamic Disks -- something you do NOT want to do.

---

