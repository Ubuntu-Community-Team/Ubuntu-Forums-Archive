---
title: "Natty wont boot after a forced restart"
date: 2011-06-26
forum: General Help
---

### Post by basilwatson on 2011-06-26
Hi all 
Was using firefox on natty 11.04 when the firefox started to think...... 

screen went darker .... then the whole system froze,,,, causing me to hit the restart button

on a restart I get the famous black screen ,,,,,, and nothing 

In with an install cd 

and the following error messages ( see below ) 

How can I restore this partition. (sda3 its where I have my bootable 11.04 

Kind regards 

Stephen..


Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so






To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

caelinux@caelinux:~$   dmesg | tail  or so
tail: cannot open `or' for reading: No such file or directory
tail: cannot open `so' for reading: No such file or directory
caelinux@caelinux:~$   dmesg | tail  
[  557.420406] Descriptor sense data with sense descriptors (in hex):
[  557.420409]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  557.420421]         62 d0 9d 98 
[  557.420426] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  557.420432] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 62 d0 9d 6e 00 01 00 00
[  557.420443] end_request: I/O error, dev sda, sector 1657839000
[  557.420465] ata2: EH complete
[  557.420486] JBD: Failed to read block at offset 2956
[  557.420492] JBD: recovery failed
[  557.420494] EXT4-fs (sda3): error loading journal
caelinux@caelinux:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000156c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       72326   580958563+  83  Linux
/dev/sda2          118614      121601    24001079+   5  Extended
/dev/sda3   *       87775      118613   247714267+  83  Linux
/dev/sda4           72327       87774   124086060   83  Linux
/dev/sda5          118614      121601    24001078+  82  Linux swap / Solaris

Partition table entries are not in disk order
caelinux@caelinux:~$

---

### Post by blueridgedog on 2011-06-26
What happens when you try to scan the disk for errors?

```
sudo fsck /dev/sda3
```

---

### Post by basilwatson on 2011-06-26
Well that did the trick , though I dont know why , and the report say there is 1 bad sector ( what does that mean?) 

anyway heres the output;

Thanks Stephen 
caelinux@caelinux:~$ sudo fsck /dev/sda3
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
ubuntu: recovering journal
Error reading block 30968716 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Clearing orphaned inode 5111862 (uid=0, gid=0, mode=0100600, size=81)
Clearing orphaned inode 5111861 (uid=1000, gid=1000, mode=0100600, size=4096)
Clearing orphaned inode 5111858 (uid=1000, gid=1000, mode=0100600, size=4096)
Clearing orphaned inode 131835 (uid=1000, gid=1000, mode=0100600, size=1)
Clearing orphaned inode 131734 (uid=1000, gid=1000, mode=0100644, size=4508)
Clearing orphaned inode 131814 (uid=1000, gid=1000, mode=0100600, size=1)
Clearing orphaned inode 131848 (uid=1000, gid=1000, mode=0100644, size=4508)
Clearing orphaned inode 131797 (uid=1000, gid=1000, mode=0100600, size=1)
Clearing orphaned inode 131862 (uid=1000, gid=1000, mode=0100644, size=4508)
Clearing orphaned inode 5111847 (uid=1000, gid=1000, mode=0100600, size=4096)
Clearing orphaned inode 5111828 (uid=1000, gid=1000, mode=0100600, size=4096)
Clearing orphaned inode 5111823 (uid=1000, gid=1000, mode=0100600, size=4096)
ubuntu: clean, 201609/15482880 files, 5447533/61928566 blocks
caelinux@caelinux:~$

---

### Post by blueridgedog on 2011-06-27
Most disks eventually develop bad sectors.  Comes with age...glad you got it sorted.

---

