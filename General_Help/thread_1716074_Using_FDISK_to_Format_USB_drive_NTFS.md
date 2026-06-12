---
title: "Using FDISK to Format USB drive NTFS"
date: 2011-03-27
forum: General Help
---

### Post by hogfan on 2011-03-27
This is giving me all kinds of issues.  I have Ubuntu server (Maverick) running and I am trying to configure some rsync Cron jobs to backup some media files and system files.    However, I formatted an external 750 GB HDD as 1 NTFS partition from the terminal using FDISK.  However when I try to mount the partition it says it's not valid NTFS.  Do I need to set any flags on the drive in FDISK first?  And if so which hex code do I choose for NTFS?  thanks

-hogfan

---

### Post by bodhi.zazen on 2011-03-28
fdisk does not format, use mkfs

In your case,

mkfs.ntfs /dev/sdxy

where /dev/sdxy is the partition to format.

---

