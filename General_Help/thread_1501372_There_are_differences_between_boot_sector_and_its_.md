---
title: "There are differences between boot sector and its backup"
date: 2010-06-04
forum: General Help
---

### Post by dhollman on 2010-06-04
Hey all,
    I'm trying to get some data off of an external harddrive.  I get a few errors:

Unable to mount
Error mounting: mount: /dev/sdb1: can't read superblock.

I then tried to run a read disk benchmark on disk utility and that seemed okay.

I then tried
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e82c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    b  W95 FAT32

```

I don't really know what all of this means!

I then tried

```
ubuntu@ubuntu:~$ sudo fsck.vfat /dev/sdb1
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00, 71:43/20, 72:41/20, 73:52/20, 74:41/20, 75:50/20, 76:41/20
  , 77:43/20, 78:45/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
Both FATs appear to be corrupt. Giving up.

```

However, I don't know which option to choose.  I just tried both of these commands after googling these errors.  I'm not a linux master and know very few commands.  Anyone have any idea?  I just want to get this data off this disk as it's quite important and I can't seem to mount it in windows or linux.

---

### Post by dhollman on 2010-06-04
okay I have an update/more information.  (This is actually a friend's harddrive).  So, this external harddrive was used on a Mac, and the user removed the drive without safely ejecting it potentially while it was in use.  Not sure how much of an effect this has, but I thought it may be important.

---

### Post by philinux on 2010-06-04
> **dhollman said:**
> okay I have an update/more information.  (This is actually a friend's harddrive).  So, this external harddrive was used on a Mac, and the user removed the drive without safely ejecting it potentially while it was in use.  Not sure how much of an effect this has, but I thought it may be important.

It's going to have to plugged back into the mac I think and give it a check disk or whatever the mac does for this. Then safely remove.

---

### Post by dhollman on 2010-06-04
Problem is, the mac cannot detect the drive anymore.

---

### Post by philinux on 2010-06-04
You are going to need testdisk/photorec then I reckon.

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

I seem to remember it's in ubuntu repos.

---

