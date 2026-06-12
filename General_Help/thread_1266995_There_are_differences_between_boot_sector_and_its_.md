---
title: "There are differences between boot sector and its backup"
date: 2009-09-15
forum: General Help
---

### Post by brallan on 2009-09-15
Does disaster await me?

The 500GB USB ntfs drive I was using to backup my data was giving me problems with filenames containing chinese characters and undeletable files, so I decided to format it and go with FAT32, just like the original, another 500GB external USB drive. The original was making gparted crash, so i decided to fsck it, and lo and behold:

```
sudo fsck /dev/sdc1
fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  1:58/5a, 65:01/00, 67:8d/1d, 68:13/3d, 69:e6/ef, 70:6f/14, 90:fa/f1
  , 91:fc/7d, 92:31/fa, 93:c0/33, 94:8e/c9, 95:d0/8e, 96:bc/d1, 97:b4/bc
  , 98:7b/f8, 99:06/7b, 100:57/8e, 101:8e/c1, 102:c0/bd, 103:b9/78, 

```
etc... etc...
```
  , 495:65/01, 496:72/00, 497:72/57, 498:6f/49, 499:72/4e, 500:0d/42
  , 501:0a/4f, 502:00/4f, 503:00/54, 504:c4/20, 505:12/53, 506:22/59
  , 507:05/53, 508:7f/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 
```

When I choose 3) no action, it continues with all sorts of errors.

This is not a boot disk, I just need the files. Is there a relation between the boot sector and the File Allocation Table?

akkk! I am desperate, as I no longer have a backup of the data, backups take many hours, and I have to get on a plane tomrrow for 6 months away!! 

what should I do?

---

### Post by brallan on 2009-09-15
This [thread]("http://www.elmodem.com/archivo/2008/05/07/there-are-differences-between-boot-sector-and-its-backup/") (in spanish) said I should first try the first option, and if that fails , then try the second.

What I don't understand, is that if I try the first option, doesn't that wipe out my backup, making it impossible to later do the second option?

---

