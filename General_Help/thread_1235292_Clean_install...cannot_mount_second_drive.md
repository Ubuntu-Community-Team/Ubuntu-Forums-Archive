---
title: "Clean install...cannot mount second drive"
date: 2009-08-08
forum: General Help
---

### Post by rayj on 2009-08-08
Hello!

I just reinstalled Ubuntu Studio 8.04. I have all of my media files on a second hard drive. I've read the Ubuntu pages concerning mounting additional drives...created a mount point for the disk, and edited my fstab...but the system still will not mount the filesystem.

I'm a bit soft on partitions and whatnot...apparently, my system sees the second hard drive as an extended partition...

Did I just lose all that data? If not, how do I go about diagnosing and addressing my issue here?


Thanks in advance...

---

### Post by rayj on 2009-08-09
Here's some output: I simply don't understand it well enough, and can't seem to find anything useful in the forums/etc.

rayj@main:~$ mount /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@computer:~$ dmesg|tail
[  535.998649] Buffer I/O error on device sr0, logical block 1310328
[  535.998652] Buffer I/O error on device sr0, logical block 1310329
[  537.391470] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  537.391475] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
[  537.391479] Info fld=0x13fe70
[  537.391480] sr 0:0:1:0: [sr0] Add. Sense: Unrecovered read error
[  537.391484] end_request: I/O error, dev sr0, sector 5241280
[26697.633044] attempt to access beyond end of device
[26697.633050] sdb1: rw=0, want=4, limit=2
[26697.633053] EXT3-fs: unable to read superblock

---

### Post by Barafu Albino Cheetah on 2009-08-09
Do ```
sudo fdisk -l /dev/sdb
``` and show us

---

### Post by rayj on 2009-08-09
fdisk gives me:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e71a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    5  Extended

---

### Post by Barafu Albino Cheetah on 2009-08-09
You have messed the disk. It is empty now. If there was something important, the specialist would be able to restore it for you, but I wouldn't try to tell you how through internet. Sorry.

---

### Post by rayj on 2009-08-09
Ah well. It's a good thing I have most of it in backups...


Thanks for the quick response!

One thing: how did you come to that conclusion? I'd like to be able to reconfigure my systems without wiping every drive...is there a link to some useful information?

---

