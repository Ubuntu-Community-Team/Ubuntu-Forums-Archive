---
title: "Unable to mount hard drives after a system crash"
date: 2009-10-10
forum: General Help
---

### Post by biggreenthugs on 2009-10-10
Hello all

Just wanted to thank in advance any and all who can help me resolve this. 

My system hung and froze. With much dread I pressed the reset button. )having done this before when the system had stopped responding and had to reinstall the os.) after the restart and the having to run fsck I was able to boot to my gnome desktop horray! till I tried to mount a /media drive and I got nothing. I run 7 physical drives inside this box (mostly from throwing old hard drives into it as I upgrade other machines laying around) which is easy because it's an old abit kt7a-raid. But I'm moving off point. Now I can't mount the extra drives. 

I'm relatively new to ubuntu and linux. I did some reading and I know I need to modify a few things. exactly what and the syntax to do so kinda scares me to be honest as I'm afraid a mistake will lead to unrecoverable data loss ( I say that like it's a big deal, I have all the important stuff achived already it's just a pain I'd rather avoid)

How do I fix this?

some notes:
all linux drives are formatted to ext3 with the following exceptions
sda1 = ext4
sdg1 = ext2

sdb1 = /boot and sdf1 = /

here is a copy of my fdisk -l
[INDENT]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007fef4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11c211c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         125     1004031   83  Linux
/dev/sdb2             126        1247     9012465   82  Linux swap / Solaris

Disk /dev/sdc: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x360c360b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2481    19928601    c  W95 FAT32 (LBA)

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bb42a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9729    78148161   83  Linux

Disk /dev/sde: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97bf083d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        4982    40017883+  83  Linux

Disk /dev/sdf: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04d4af84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        4865    39078081   83  Linux

Disk /dev/sdg: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeebfd118

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       14593   117218241   83  Linux

[/INDENT]and here's fstab
[INDENT]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde1 during installation
UUID=9d46a9cb-75b9-4990-952f-726431f6aaf9 /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=8b4e0679-266f-44bc-afe7-6271de275a69 /boot           ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=ae781914-7f8e-4e16-9bf7-d478b3b81417 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[/INDENT]and mtab
[INDENT]/dev/sdf1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-15-generic/volatile tmpfs rw,mode=755 0 0
/dev/sdb1 /boot ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jknowles/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jknowles 0 0
[/INDENT]

---

