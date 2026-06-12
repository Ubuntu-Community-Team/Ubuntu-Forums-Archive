---
title: "System required restart, drive will no longer mount"
date: 2010-03-25
forum: General Help
---

### Post by d0wnthe11235813 on 2010-03-25
I have an old computer that i use as a file server, nothing special, its an old laptop that is quiet and low power.  i SSHed into it a few days ago and it said it needed a reboot, and thus i did and forgot about it until that night.  later i tried to watch a video i had on a USB HDD attached to the laptop and couldnt, SSHed in and found that the drive didnt mount, tried to mount the drive with ```
sudo mount /dev/sdb1 /storage2
``` and it returned ```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail  or so
```dmesg | tail returned:
```
[11144.674278] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027
[11144.724118] EXT3-fs: no journal found.
[11158.256067] sd 2:0:0:0: [sdb] Unhandled sense code
[11158.256074] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11158.256080] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[11158.256087] Info fld=0x0
[11158.256090] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[11158.256097] end_request: I/O error, dev sdb, sector 8279
[11158.258331] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027
[11158.332154] EXT3-fs: no journal found.
```cat /proc/partitions spits out:
```
major minor  #blocks  name

   8        0  117220824 sda
   8        1    9767488 sda1
   8        2          1 sda2
   8        5    1951866 sda5
   8        6     979933 sda6
   8        7    4883728 sda7
   8        8    9767488 sda8
   8        9    2931831 sda9
   8       10   19535008 sda10
   8       16  488386584 sdb
   8       17  488384001 sdb1
```i've been reading a lot of threads here and many mentioned testdisk.  I used testdisk to rebuild the MBR and that didnt help either.  I used testdisk to grab the superblocks and sudo /sbin/fsck.ext2 -b 98304 /dev/sdb1 to (i believe) rebuild the file system only to no success.

now i know i am an idiot and didnt backup any of this stuff.  the drive is only around 3 months old.  any help or suggestions.  none of the data that is lost is mission critical but it is roughly the highlights of the last 10 or so years of me and my computing so if there is any chance that i could save this stuff i will make the helper cookies...or beer...or something

---

### Post by dcstar on 2010-03-25
> **d0wnthe11235813 said:**
> I have an old computer that i use as a file server, nothing special, its an old laptop that is quiet and low power.  i SSHed into it a few days ago and it said it needed a reboot, and thus i did and forgot about it until that night.  later i tried to watch a video i had on a USB HDD attached to the laptop and couldnt, SSHed in and found that the drive didnt mount, tried to mount the drive with ```
sudo mount /dev/sdb1 /storage2
``` and it returned ```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail  or so
```dmesg | tail returned:
```
[11144.674278] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027
[11144.724118] EXT3-fs: no journal found.
[11158.256067] sd 2:0:0:0: [sdb] Unhandled sense code
[11158.256074] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11158.256080] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[11158.256087] Info fld=0x0
[B][11158.256090] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[11158.256097] end_request: I/O error, dev sdb, sector 8279[/B]
[11158.258331] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027
[11158.332154] EXT3-fs: no journal found.
```


USB drives die, this one is dead.

---

