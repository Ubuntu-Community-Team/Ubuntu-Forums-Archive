---
title: "trouble with firewire hard drive"
date: 2010-02-01
forum: General Help
---

### Post by Dilutu on 2010-02-01
Hi all!
In karmic,when I plug in my firewire hard drive (working fine with hardy),I get this message: " Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

syslog shows : "server kernel: [   30.168898] FAT: bogus number of reserved sectors
 server kernel: [   30.168907] VFS: Can't find a valid FAT filesystem on dev sdd1."

sudo fdisk -l gives : "Disk /dev/sdd: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f78e9ea
Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9964    80035798+   7  HPFS/NTFS "

What could be wrong???...Th.

---

### Post by jamesisin on 2010-02-01
I am seeing a similar issue only on the OS partition:

[http://ubuntuforums.org/showthread.php?t=1396158](http://ubuntuforums.org/showthread.php?t=1396158)

You may want to add information to your thread such as I have on my thread.

---

### Post by Dilutu on 2010-02-01
Solved!
I found an entry in fstab with the wrong file system for sdd1. After removing that entry, I 'm able to access this drive!...Th.

---

### Post by jamesisin on 2010-02-01
Wish mine was that easy...

Remember to mark this thread as SOLVED in Thread Tools above.

---

