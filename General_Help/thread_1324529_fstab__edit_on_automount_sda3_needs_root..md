---
title: "fstab  edit on automount sda3 needs root."
date: 2009-11-12
forum: General Help
---

### Post by Sico2 on 2009-11-12
Since I used Ubuntu I always edited fstab to automount my second partition with media. I simply added this line:

```
/dev/sda3 /media/disk           ext3    defaults        0       2
```

Now, when I do it, the system says I have no root privileges to mount the drive. Until I delete this line again I can't mount the partition.

fdisk-l:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x359c3e6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2           29646       30401     6072570    f  W95 Ext'd (LBA)
/dev/sda3            3825       29645   207407182+  83  Linux
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

```

Did anything change in 9.10 since then?

---

### Post by jbrown96 on 2009-11-12
Does /media/disk exist? That's usually a folder that gets created when you insert a flash drive. Perhaps you need to create the folder, or maybe something else is try to mount there.

---

### Post by Sico2 on 2009-11-13
the /media/disk does not exist, but you can name whatever you want the partition. I did 212Gb, but still changing it means root privileges to mount.

I did not have to enter the root password mounting manually on 9.04 for the partition, now I do. :/

---

### Post by mosaic2s on 2009-11-19
I have same issue in 9.10.
The fstab is mounting ntfs but ext3 and ext4 on other partitions need root. Can not resolve this.

---

### Post by ricardo.gloe on 2009-11-19
Ubuntu Karmic Koala 9.10 uses UUID by default (Jaunty did not), so when you include other disks/partitions in fstab, you have to identify them using their UUID. 

*I don't know if that's the solution to your problem but I noticed Sico2's fstab wasn't using UUID. *

See my fstab: 

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=247e3b5b-f691-4dca-98e2-08a44c5b6a68 / ext4 defaults,noatime,nobh,data=writeback,commit=100,barrier=0,nouser_xattr 0 1
# /boot was on /dev/sda1 during installation
UUID=23b55cdd-2e88-4309-badf-87dde21efcbc /boot ext4 defaults,noatime,nobh,data=writeback,commit=100,barrier=0,nouser_xattr 0 2
# /home was on /dev/sda7 during installation
UUID=c3e6de70-41e7-49b7-a7ba-ea96887d2cf5 /home ext4 defaults,noatime,nobh,data=writeback,commit=100,barrier=0,nouser_xattr 0       2
# swap was on /dev/sda6 during installation
UUID=2f41a077-b004-4dad-9b94-a5a523d5007a none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0
# 2nd HD
[COLOR="Red"]UUID=96aeae01-3852-4cfb-8739-204f2c1aa099 /media/BKP ext4[/COLOR] defaults,noatime,nobh,data=writeback,commit=100,barrier=0,nouser_xattr 0 2
```

To see your disk/partitions' UUID, use [HTML]blkid[/HTML], as stated in fstab. 

Hope it helps!

---

### Post by mosaic2s on 2009-11-20
thanks ricardo.
Used UUID of the sda1 and sda2 from gparted. And added part of the fstab given by you.

It is working.

---

