---
title: "Can mount a installed hard drive. Lost all my stuff!"
date: 2010-01-24
forum: General Help
---

### Post by jman316 on 2010-01-24
Hi,

I was trying to install a new hard drive and in the process have managed to not only format my old hard drive but lost all my stuff as well. I am running  a live CD but unable to mount the said hard drive. I Know its there.  fdisk tells me:

Disk **/dev/sda**: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ab32ab3

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03e803e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1120     8996368+  83  Linux
/dev/sdb2            1121        1369     2000092+  82  Linux swap / Solaris
/dev/sdb3            1370        4998    29149942+  83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f27c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1245    10000431   83  Linux

As you can see its still registering as /dev/sda, I am unable to mount this to run a undelete program on it.

a e2fsck tells me

e2fsck /dev/sda
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Permission denied while trying to open /dev/sda
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Please help me....what can i do?

i hope this makes sense....

---

### Post by oldos2er on 2010-01-24
It looks like sda has no partitions which could be mounted, which makes sense if it's new.

---

### Post by jman316 on 2010-01-25
> **oldos2er said:**
> It looks like sda has no partitions which could be mounted, which makes sense if it's new.

Its not new though, i think this is the hard drive i formatted by accident. But i cant see it mounted either!!!

---

### Post by jman316 on 2010-01-25
Please advise me on the best i can recover my stuff from this drive?

---

### Post by oldos2er on 2010-01-25
So the other three Linux partitions don't contain the data you're looking for?

---

