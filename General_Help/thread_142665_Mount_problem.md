---
title: "Mount problem"
date: 2006-03-10
forum: General Help
---

### Post by Moonhill on 2006-03-10
I have XP installed on 1st SATA hdd /dev/sda1 and ubuntu on 2nd SATA hdd /dev/sdb1.

When I try to mount XP, it says 'already mounted or busy'.

Of course I put it in /etc/fstab, too. But it just doesn't work. How can I mount it? Is it problem of two SATA hdd?

Thanks.

---

### Post by taurus on 2006-03-10
What is the content of your /etc/fstab and what is the output of "df -h" from the command prompt?

---

### Post by Moonhill on 2006-03-11
/etc/fstab :
/dev/sda1       /home/kisoo/xp     ntfs ro,user,nls=cp949,utf8,umask=0222

$df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             144G  3.6G  134G   3% /
tmpfs                 506M     0  506M   0% /dev/shm
tmpfs                 506M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile
/dev/fd0              1.4M  280K  1.2M  20% /media/floppy0
/dev/sdc1             248M  122M  127M  50% /media/usbdisk

---

### Post by taurus on 2006-03-11
You plan to  mount your XP inside your home directory!!!  You are missing 0 0 at the end of it...
```

/dev/sda1 /home/kisoo/xp ntfs ro,user,nls=cp949,utf8,umask=0222 0 0

```

---

### Post by tOpEzz on 2006-03-11
no wonder u cannot mount... dont forget ur 0 0 dude. good luck!!

---

### Post by sYs^ on 2006-03-13
I have a similar problem, i have 3 HDDs, on hdc i have 4 partitions:

- one for windows xp
- one for ubuntu
- one for unbuntu swap
- and another ntfs

When i want to mount the windows xp's partition and the ntfs (on hdc) everything is o.k. 

But when i want to mount the two other partitions on the two other HDD, it fails.

mount /dev/hda1
mount: /dev/hda1 already mounted or /home/dani/windows/d busy

and

mount /dev/hdb1
mount: /dev/hdb1 already mounted or /home/dani/windows/f busy

My fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/hdc1       /home/dani/windows/c ntfs ro,user,nls=cp949,utf8,umask=0222 0 0
/dev/hdc5       /home/dani/windows/g ntfs ro,user,nls=cp949,utf8,umask=0222 0 0
/dev/hdb1       /home/dani/windows/f ntfs ro,user,nls=cp949,utf8,umask=0222 0 0
/dev/hda1       /home/dani/windows/d ntfs ro,user,nls=cp949,utf8,umask=0222 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy1  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy2  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy3  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy4  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy5  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy6  auto    rw,user,noauto  0       0

```

fdisk -l:
```
Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+   7  HPFS/NTFS

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1399    11237436    7  HPFS/NTFS
/dev/hdc2            3722       14945    90156780    f  W95 Ext'd (LBA)
/dev/hdc3            1400        3721    18651465   83  Linux
/dev/hdc5            3825       14945    89329401    7  HPFS/NTFS
/dev/hdc6            3722        3824      827284+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

When Ubuntu starts there are two error messages:
mount: unknown filesystem type :'devfs'
umount: devfs: not mounted

mount: unknown filesystem type :'devfs'
umount: devfs: not mounted

My kernel is:
```
Linux ubuntu 2.6.15.6 #1 PREEMPT Sun Mar 12 22:15:56 CET 2006 i686 GNU/Linux
```

Any ideas?

---

