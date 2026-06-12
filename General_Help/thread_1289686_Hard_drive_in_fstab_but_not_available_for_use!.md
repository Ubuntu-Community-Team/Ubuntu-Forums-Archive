---
title: "Hard drive in fstab but not available for use!"
date: 2009-10-12
forum: General Help
---

### Post by Teabicky on 2009-10-12
Hi,

I am using Mint (Gloria) which is based on Jaunty. I think that my problem is the same using either Mint or Ubuntu and I will post any solutions on the Mint forum.

I have tried to mount a partition of an extra internal hard drive for storage of all of my files (music etc), in fstab.  The partition that I am trying to mount is dev/sdb1 and I have put it into fstab like so:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9e9b26a5-29ca-461d-b6c3-395a181de53c /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=4b4600af-ba7e-4531-9203-a5fdff153ce7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb1	/media/linux	ext4	defaults	0	0

After I did this I restarted my computer and nothing happened.  The partition still shows up in "computer" but it will not let me open it.  Also it does not appear in /media.

What have I done wrong?


Here is my fdisk -l

> Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10250    82333093+  83  Linux
/dev/sda2   *       10251       19192    71826615    7  HPFS/NTFS
/dev/sda4           19193       19452     2088450   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009a43c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           57640      121601   513774765   83  Linux
/dev/sdb2               1       57639   462985236    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7621

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    b  W95 FAT32

---

### Post by fooman on 2009-10-12
> **Teabicky said:**
> 
After I did this I restarted my computer and nothing happened.  The partition still shows up in "computer" but it will not let me open it.  Also it does not appear in /media.


did you create the directory in /media?

like this:

```
sudo mkdir /media/linux
```

then:

```
sudo mount -a
```

then try it again.  should not have to reboot.

---

### Post by Teabicky on 2009-10-12
Excellent! That worked, Thanks.....

there is, however a further problem (which I am sure will be just as easy to solve).

When I tried to copy a folder into it I get this error message

> The folder "Back up for distro upgrades" cannot be copied because you do not have permissions to create it in the destination.

How do I change the permissions?

(I am just being lazy now)

---

### Post by Teabicky on 2009-10-13
I have started a thread enquiring about the permissions issue mentioned in the above post here:

[http://ubuntuforums.org/showthread.php?t=1290434](http://ubuntuforums.org/showthread.php?t=1290434)

---

