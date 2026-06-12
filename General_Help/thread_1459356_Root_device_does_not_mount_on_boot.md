---
title: "Root device does not mount on boot"
date: 2010-04-21
forum: General Help
---

### Post by dustingram on 2010-04-21
On boot, I get:
```

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/: waiting for /dev/md0
/tmp: waiting for (null)
Press ESC to enter a recovery shell
```

Entering the recovery shell, I can successfully mount the drive with:
```
root@primer:~# mount -o remount,rw /
```

Then, pressing CTRL-D to retry successfully boots the system. At the moment, I'm thinking the issue is that the drive does not have a UUID. My fstab looks like this:

```

dustin@primer:~$ cat /etc/fstab
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
UUID=7fbb9b30-fe0d-4930-8263-aa71a5c53c8e / ext3 relatime,errors=remount-ro 0 1
UUID=f8b1fe35-c88b-402a-9795-428b15d74464 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```

While the output of blkid and by-uuid don't show the root device:

```

dustin@primer:~$ sudo blkid
/dev/sda1: UUID="9535a860-39ff-39d5-8e09-cced080997f0" TYPE="linux_raid_member" 
/dev/sda5: UUID="832267cd-5107-cd5c-ffac-0455132f9ab7" TYPE="linux_raid_member" 
/dev/sdb1: UUID="9535a860-39ff-39d5-8e09-cced080997f0" TYPE="linux_raid_member" 
/dev/sdb5: UUID="832267cd-5107-cd5c-ffac-0455132f9ab7" TYPE="linux_raid_member" 
/dev/md1: UUID="f8b1fe35-c88b-402a-9795-428b15d74464" TYPE="swap"

```

```

dustin@primer:~$ ls -lh /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root  9 2010-04-20 19:38 f8b1fe35-c88b-402a-9795-428b15d74464 -> ../../md1

```

```

dustin@primer:~$ cat /boot/grub/menu.lst
default		0
timeout		3
hiddenmenu

title		Ubuntu 9.10, kernel 2.6.31-20-generic, hd0
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-20-generic root=/dev/md0 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic, hd1
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.31-20-generic root=/dev/md0 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode), hd0
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-20-generic root=/dev/md0 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode), hd1
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.31-20-generic root=/dev/md0 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

```

The potentially tricky thing here is that, as you may have noticed, I'm using mdadm to create a two-disk software RAID 1. The root device is /dev/md0 and the swap device is /dev/md1. However, all drives/partitions look fine:

```

dustin@primer:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Jun 27 11:52:35 2009
     Raid Level : raid1
     Array Size : 728708288 (694.95 GiB 746.20 GB)
  Used Dev Size : 728708288 (694.95 GiB 746.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Apr 21 10:27:53 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 9535a860:39ff39d5:8e09cced:080997f0
         Events : 0.2966914

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

```

I've tried a number of things, resetting the UUID with tune2fs, and changing the UUIDs in /etc/fstab with the drive labels, but nothing seems to work. This isn't exactly a pressing issue now that I'm able to boot my system, but I don't want to have to go through the recovery shell every time.

Also I should not that this is NOT related to the [mountall bug]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/459859") referenced in [this thread]("http://ubuntuforums.org/showthread.php?t=1301766") (i.e., my system never boots if I leave it).

Any help would be greatly appreciated!

EDIT: System info:
```

dustin@primer:~$ uname -a
Linux primer 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

```

---

