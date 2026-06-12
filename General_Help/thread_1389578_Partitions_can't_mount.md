---
title: "Partitions can't mount"
date: 2010-01-24
forum: General Help
---

### Post by ubv1308 on 2010-01-24
[9.04] So the computer crash and I restarted, now boot,swap and home mount but I can't mount my other three partitions. (added to fstab manually, working for months). GParted can see them but cannot mount them.

No idea what to try next, here's my fdisk and fstab.

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31f2e2f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6104    49030348+  83  Linux
/dev/sda2            6105      121601   927729652+   5  Extended
/dev/sda5            6105        6870     6152863+  82  Linux swap / Solaris
/dev/sda6            6871       11733    39062016   83  Linux
/dev/sda7           11734      121601   882514678+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eea5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       40145   322464681   83  Linux
/dev/sdb2           40146      121601   654295320    5  Extended
/dev/sdb5           40146      121601   654295288+  83  Linux

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=679d51ba-de27-42af-98b9-64459bdf1e19  /                ext3         relatime,errors=remount-ro  0  1  
# /home was on /dev/sda6 during installation
/dev/sdb1                                  /enregistrement  jfs          relatime                    0  2  
UUID=fc9dd78f-fe7d-4168-93d6-f2eeac0aae9a  /home            ext3         relatime                    0  2  
# swap was on /dev/sda5 during installation
UUID=5a49de9b-5efe-4288-8347-655df4dfcbc4  none             swap         sw                          0  0  
/dev/sda7                                  /storage         jfs          relatime                    0  2  
/dev/sdb5                                  /video           jfs          relatime                    0  2  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0   auto         rw,user,noauto,exec,utf8    0  0

---

### Post by ubv1308 on 2010-01-24
If I do "sudo mount -a", I get this (pretty general) error :
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg give me this :
[  136.500441] Clocksource tsc unstable (delta = -133219693 ns)
[ 227.729759] JFS : nTxBlock = 8192, nTxLock = 65536

I can't run fsck either (with JFS Utils installed), I get :
Error: Cannot open device /dev/sdb1

Anybody got an idea how to fix it ?

---

