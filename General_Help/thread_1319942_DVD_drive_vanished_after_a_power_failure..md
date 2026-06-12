---
title: "DVD drive vanished after a power failure."
date: 2009-11-08
forum: General Help
---

### Post by seamus_android on 2009-11-08
My flatmate spilled wine over her laptop power supply and tripped tripped the ring main circuit breakers.  My PC powered down immediately, but when it came back up, it was no longer able to find my DVD drive.

My first thought was that despite the allegedly surge protected gang I had had a hardware failure, but I was able to boot from a live disk.  The problem only happens when booting into my main ubuntu system.

fdisk -l:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8a17b7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2334    18747823+  83  Linux
/dev/sda2            2335       64581   499999027+  83  Linux
/dev/sda3           64582       65554     7815622+  82  Linux swap / Solaris
/dev/sda4   *       65555       98700   266240000    7  HPFS/NTFS
```

/etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=36db37b5-db82-410b-9edd-e1ad27a7a0c1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=5a70ac58-6d21-422c-8bc2-3e8dfbbaf270 /home           ext3    defaults        0       2
/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

/dev/scd0 does not exist.  At the time the power went I was burning 500MB of very, very boring XML files to CD-RW.

I am running 9.10 64-bit.  Thanks in advance.

---

