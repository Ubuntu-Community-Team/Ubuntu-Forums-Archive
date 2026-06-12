---
title: "Unable to delete or reformat partition"
date: 2012-05-01
forum: General Help
---

### Post by b k on 2012-05-01
The current problem I am facing arose from a failed installation of Edubuntu 12.04 (from an .iso image on an bootable usb flash stick) to a desktop ide Maxtor 30 gb hdd.
The Maxtor drive was freshly formatted to fat32 without any issues on another WinXP machine prior to the failed install.
Gparted was used to create 2 partitions during the failed installed. I can see the two partitions but am unable to delete and reformat.

The Maxtor drive was then detached and is now plugged in (as slave) on another computer running Ubuntu 12.04.
Running Gparted on a bootable usb stick produced the same results.
The drive is currently /dev/sdb.

Error message from within Gparted reads :
liparted message
Input/output error during write on /dev/sdb
Error fsyncing/closing /dev/sdb: input/output error

Other messages from Terminal are:

user@XXX:~$ sudo fsck /dev/sdb
[sudo] password for user: 
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

user@XXX:~$ sudo fsck /dev/sdb1
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: No such file or directory while trying to open /dev/sdb1
Possibly non-existent device?


user@XXX:~$ sudo tune2fs -l /dev/sdb
tune2fs 1.42 (29-Nov-2011)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock.
user@XXX:~$ sudo tune2fs -l /dev/sdb1
tune2fs 1.42 (29-Nov-2011)
tune2fs: No such file or directory while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.


I am just wanting to reformat the whole drive but normal ways of doing it is not working.
My gut instinct also tells me that there is nothing wrong physically with the drive.
Any help would be most appreciated.
Thanks

---

