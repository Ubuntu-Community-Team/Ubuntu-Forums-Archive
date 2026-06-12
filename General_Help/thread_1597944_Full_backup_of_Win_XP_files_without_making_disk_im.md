---
title: "Full backup of Win XP files without making disk image"
date: 2010-10-15
forum: General Help
---

### Post by bakegoodz on 2010-10-15
--------------Background-----------

The NTFS on my XP computer has some strange NTFS file-system problem doesn't seem to affect anything, but chkdsk reports unrecoverable error. and I want to backup the whole drive C: I need to do it by copying the just the files, not the damaged file-system. 

- Disk is physically fine, no bad sectors
- Tried Clonezilla and Ghost they just copy the same NTFS problem over to another drive.
- I've tried several Partition resize, and defrage programs they all fail and give some type of NTFS attribute or meta-data error.
- Windows boots up fine, all programs work fine
- CHKDSK says it can't repair it.

I determined that I need to copy all of the files off, reformat partition and copy the files back. Planing on using a NTFS formated external drive to backup to.

------------------Here is the Question------------------

1. Can Linux make a full file based copy of all the files and file attributes from one Windows system partition to another without problems? (granted all the MBR and boot stuff is set right.)

2. What is a good console command to do this?

---

### Post by bakegoodz on 2010-10-17
Haven't got an answer, so I decided to just try it. I used System Recovery Linux which has the latest ntfs-3g driver. Used the command: cp -r -p /mnt/windows /mnt/custom/backup (Recursive copy with Preserve ownership time stamps)
It took several hours to backup and restore all data, and of course reformatted the drive too.
But it worked! Woohoo!

---

