---
title: "Can't access external hard drive"
date: 2011-11-22
forum: General Help
---

### Post by aronstandley on 2011-11-22
Hey folks,

I'm trying to get into my external hard drive, but it's not recognizing the file system as a folder.

I was having difficulty, before this happened, in transferring files to the hard drive, because of permissions - it was a read-only file system, so I tried changing the passwords of the hard drive through sudo.

How can I remedy this?

---

### Post by Mark Phelps on 2011-11-22
How is the hard drive formatted?

If you don't know, next time you connect up the drive, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).

That will list off the partitions, including the external drive.

If the drive is partitioned NTFS, and you did not "Safely Remove" it the last time it was used, then Ubuntu will default to mounting it read-only to protect the integrity of the filesystem.

In that case, you will need to connect the drive to a Windows PC and run CHKDSK on it.  THEN, safely remove it from the Windows PC.

---

