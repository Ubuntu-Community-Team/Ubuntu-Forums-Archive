---
title: "how mount raid"
date: 2010-03-08
forum: General Help
---

### Post by DaveJL on 2010-03-08
Hello,

To try to fix my system, I am in the Recovery Mode (Ubuntu 8.04.3 LTS, "hardy") on my server.  I am trying to mount the filesystem to be able to edit the system configuration files of my normal system.

fdisk -l shows the following:

```
# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c6cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   fd  Linux raid autodetect
/dev/sda2              14         655     5156865   82  Linux swap / Solaris
/dev/sda3             656       60801   483122745   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002ec98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   fd  Linux raid autodetect
/dev/sdb2              14         655     5156865   82  Linux swap / Solaris
/dev/sdb3             656       60801   483122745   fd  Linux raid autodetect
```When I try to mount sda3, I get:

```
# mount /dev/sda3 /mnt
mount: unknown filesystem type 'linux_raid_member'
```I tried searching on google and this forum for keywords to get guidance how to proceed, but I haven't found anything that works.  So, I would sincerely appreciate if a kind soul could point me in the right direction.

Thanks much,
Dave

---

### Post by DaveJL on 2010-03-08
I tried a couple more commands:

```
# modprobe raid1
# mdadm -E -s
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=629bfb37:53a8883f:537f768e:e9290991
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=adc78fa5:fac6da39:5ea2599b:29ca6912

```

Please guide me as to what I need to do with this information in order to mount my RAID disks and be able to edit my normal system configuration files.

Thanks,
Dave

---

### Post by richardjh on 2010-03-08
It looks like the raid devices are already assembled, which makes it a bit easier.

I guess you have sda1 and sdb1 RAIDed as md0 and sda3 and sdb3 RAIDed as md1
md0 is probably your /boot partition given that it is 100MB.

So the interesting stuff is probably on md1

You should be able to mount the devices but use /dev/md1 not /dev/sda3.

For example

```
mount /dev/md1 /mnt/
```

---

### Post by DaveJL on 2010-03-08
Thanks, it worked ...

Now my next problem, which is the larger problem, why I had to be in Recovery Mode in the first place ... 

Upon booting up, everything hangs after "RAID1 conf printout:" ...

```
raid1: raid set md0 active with 2 out of 2 mirrors
md: ... autorun DONE.
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
SELinux:  Disabled at runtime.
type=1404 audit(1268063367.600:2): selinux=0 auid=4294967295 ses=4294967295
RAID1 conf printout:
 --- wd:2 rd:2
 disk 0, wo:0, o:1, dev:sda3
 disk 1, wo:0, o:1, dev:sdb3

```

This boot hanging problem started after I ran /etc/rc.d/rc.sysinit to reset the hostname, but the power went out before the script completed.

I'm suspecting that the hard kill messed up some boot files, and I'm hoping a kind & wise soul can help guide me on how to restore them properly, now that I can mount & edit my files in Recovery Mode.

Thanks very much.
Dave

---

### Post by DaveJL on 2010-03-08
I'm now in Recovery Mode.

My /etc/fstab :

```

/dev/md1                /                       ext3    defaults,usrquota        1 1
/dev/md0                /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=SWAP-sdb2         swap                    swap    defaults        0 0
LABEL=SWAP-sda2         swap                    swap    defaults        0 0
```


fdisk -l yields:

```
# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c6cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   fd  Linux raid autodetect
/dev/sda2              14         655     5156865   82  Linux swap / Solaris
/dev/sda3             656       60801   483122745   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002ec98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   fd  Linux raid autodetect
/dev/sdb2              14         655     5156865   82  Linux swap / Solaris
/dev/sdb3             656       60801   483122745   fd  Linux raid autodetect

Disk /dev/md1: 494.7 GB, 494717566976 bytes
2 heads, 4 sectors/track, 120780656 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
```mdadm -E -s shows:

```

# mdadm -E -s
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=629bfb37:53a8883f:537f768e:e9290991
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=adc78fa5:fac6da39:5ea2599b:29ca6912
```When I try to mount /dev/md0, I get the error:

```
# mount -t ext3 /dev/md0 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```dmesg | tail shows:

```
# dmesg | tail
[ 1349.012161] unionfs: new lower inode mtime (bindex=0, name=mdadm)
[ 1356.803854] md: md1 still in use.
[ 1356.870311] md: bind<sdb3>
[ 1356.906846] raid1: raid set md1 active with 1 out of 2 mirrors
[ 1356.906867] md1: detected capacity change from 0 to 494717566976
[ 1356.906978]  md1: unknown partition table
[ 1389.504015] EXT4-fs (md0): unable to read superblock
[ 1398.655582] EXT3-fs: unable to read superblock
[ 1808.394513] EXT2-fs: unable to read superblock
[ 1836.473091] EXT3-fs: unable to read superblock
```When I try to fsck /dev/md0, I get:

```
# fsck /dev/md0
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Invalid argument while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```I'm not sure how to proceed ... any guidance would be much appreciated.

Thanks,
Dave

---

### Post by richardjh on 2010-03-09
This isn't a simple thing to do but can be recovered by reformatting the /boot partition on /dev/md0 and manually restoring files from the rescue CD and apt.

[This link describes a successful attempt]("http://ubuntuforums.org/showthread.php?t=306617")

I would recommend that you take the opportunity to backup all of your important stuff to USB drive or another machine and then reinstall. 
I know this is not the best solution but is far simpler to achieve.

It depends on your circumstances.

---

### Post by DaveJL on 2010-03-09
Thanks Richard,

As it turns out, I had a corrupted superblock in my boot drive (/dev/md0) which I was able to repair using fsck.

However, after rebooting, the same boot-up problem (hanging for hours) persists.

When I re-enter Recovery Mode to examine the boot drive, I found its superblock was corrupted again (which I fixed again using fsck).

Is there a proper reboot procedure which is gentle on the boot drive, such that it doesn't corrupt it?  Or, is something else amiss?

Thanks,
Dave

---

