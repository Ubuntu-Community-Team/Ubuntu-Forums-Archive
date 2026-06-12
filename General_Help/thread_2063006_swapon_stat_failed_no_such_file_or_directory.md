---
title: "swapon: stat failed: no such file or directory"
date: 2012-09-26
forum: General Help
---

### Post by Vuk Serbia on 2012-09-26
Hi,

I have this problem with my swap partition.
I tried to do 
```
swapon /dev/sda8
```
But i got 
```
swapon: /dev/sda8: stat failed: No such file or directory

```

So i checked /etc/fstab and fdisk -l
There is swap partition at /dev/sda8 and I can see it from gParted but when I try to swapon from gParted i get an error.


Has anyone had this problem before?
Thanks in advance

---

### Post by prshah on 2012-09-26
> **Vuk Serbia said:**
> 
```
swapon /dev/sda8
```
But i got 
```
swapon: /dev/sda8: stat failed: No such file or directory

```

Please post your fdisk -l output. It is unlikely that your device name is correct.

This error message can only appear when device name is incorrect / invalid / non-existing.

Attempting to swapon without sudo (as you seem to be doing above) will produce a different error message (permission denied).

Please post your fdisk -l output, as well as /etc/fstab if you are using it (/etc/fstab is no longer required since 11.04 onwards).

Or, for a quick solution, use ```
sudo swapon -a
``` which will automatically activate all swap partitions it finds.

---

### Post by Vuk Serbia on 2012-09-26
Thank you for replying.

Here is my fdisk 
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf18e5c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20973567    10485760    c  W95 FAT32 (LBA)
/dev/sda2        20973568    21178367      102400    7  HPFS/NTFS/exFAT
/dev/sda3        21178368   210126847    94474240    7  HPFS/NTFS/exFAT
/dev/sda4       210128895   625141743   207506424+   f  W95 Ext'd (LBA)
/dev/sda5       210128896   270127103    29999104   83  Linux
/dev/sda6       270129152   314984447    22427648   83  Linux
/dev/sda7       314986496   621094911   153054208    7  HPFS/NTFS/exFAT
/dev/sda8       621096960   625139711     2021376   82  Linux swap / Solaris

```

And here is fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8ae54a76-2b71-4a66-ad66-e85d48a30dc3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=acdedb0a-a2a5-48d4-b1cc-ec47e3fa130d /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=fc7214dc-c6b4-4160-827e-cc1cceeff3a0 none            swap    sw              0       0
```

Also, when I tried to do sudo swapon -a, I get this: 
```
swapon: cannot find the device for UUID=fc7214dc-c6b4-4160-827e-cc1cceeff3a0

```

And I have attached gparted screenshot, so maybe you can get some idea from it.

---

### Post by prshah on 2012-09-26
> **Vuk Serbia said:**
> 
Also, when I tried to do sudo swapon -a, I get this: 
```
swapon: cannot find the device for UUID=fc7214dc-c6b4-4160-827e-cc1cceeff3a0

```

Your UUID for the swap partition is probably wrong. Find the correct UUID using the blkid command```
sudo blkid /dev/sda8
```

Replace the discovered UUID in your /etc/fstab file (modify existing swap entry).

Or you can simply remove the swap entry from your /etc/fstab altogether, and then successfully use swapon -a.

---

### Post by Vuk Serbia on 2012-09-26
Ok, here is what I did:

I have removed swap entry from fstab, and tried to do ```
sudo swapon -a
```

New entry hadn't been written to fstab. Instead I got this error from attachment. Error reffers to /dev/sda7 (attachment from previous post)

Edit: 
Also, here is content of mtab
```
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda6 /home ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/vuk/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=vuk 0 0
```

---

### Post by prshah on 2012-09-26
> **Vuk Serbia said:**
> 
I have removed swap entry from fstab, and tried to do ```
sudo swapon -a
```

You have to restart the system for changes made to /etc/fstab to take effect.

Why is it suddenly trying to use /dev/sda7 instead of /dev/sda8? What change have you made to your /etc/fstab?

---

### Post by Vuk Serbia on 2012-09-26
It isn't trying to use /dev/sda7 but that error appeared after i tried to set sda8 as swap.
Maybe partitions are overlaping or something like that, but it wasn't like that before.

I guess it could also be that hard disk is failing.

---

