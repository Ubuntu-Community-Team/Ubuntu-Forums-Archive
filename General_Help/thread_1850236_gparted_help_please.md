---
title: "gparted help please"
date: 2011-09-26
forum: General Help
---

### Post by liquidmonkey on 2011-09-26
i'm trying to partition an external HDD (western digital my passport).
the main partition is already there (of course) and is in NTFS.
i'm using 11.04.

when i run gparted, an information box comes up telling me that the WD passport is in NTFS and that i need 'ntfsprogs' but that is weird as its installed by default, or?

2b sure i did the whole 'sudo apt-get install ntfsprogs' and was told that its already installed.

and even after restarting linux i'm still getting the same message so i can't create a FAT32 which is what i need in order to use clonezilla to make a backup.


any ideas?
thanks :)

---

### Post by papibe on 2011-09-26
That is very unusual, why do you need to format that disc to FAT32?

Not that you are doing something wrong necessarily, but I have an inkling that may be another solution.

Are you trying to install clonezilla in that disk?
That is why you need to format it to FAT?

If so, it is a very unusual setup. I would recommend to install Clonezilla in an independent CD or USB stick, but not in the hard drive.

Is that make sense to you?
Regards.

---

### Post by liquidmonkey on 2011-09-26
> **papibe said:**
> That is very unusual, why do you need to format that disc to FAT32?

Not that you are doing something wrong necessarily, but I have an inkling that may be another solution.

Are you trying to install clonezilla in that disk?
That is why you need to format it to FAT?

If so, it is a very unusual setup. I would recommend to install Clonezilla in an independent CD or USB stick, but not in the hard drive.

Is that make sense to you?
Regards.


the 'my passport' (which is an external HDD) is 1TB in size, and i want to make a new partition, 100gig, so i can store backups of two different linux  systems on it.
the original file system is NTFS and this new partition must be FAT32 in order for clonezilla to work.

---

### Post by Mark Phelps on 2011-09-26
> **liquidmonkey said:**
> ...
the original file system is NTFS and this new partition must be FAT32 in order for clonezilla to work.

Not in my experience ...

If you want to back up Linux stuff, you would do better creating Ext4 partition(s) on your external drive.  That way, file settings and permissions are retained in the backup.

---

### Post by SecretCode on 2011-09-26
How do you intend to use clonezilla? I have saved (and restored from) clonezilla images on an external ntfs drive, with no problem.

---

### Post by liquidmonkey on 2011-09-26
this was a misunderstanding on my part i suppose.
in order to create the clonezilla live usb, it (the usb) needed to be fat32.

the actual backup image was from ubuntu in ext4 and i saved that onto my ext HDD which is ntfs.

will try and restore (as a practice) tomorrow and c if it all works.

thanks for all the help!

---

