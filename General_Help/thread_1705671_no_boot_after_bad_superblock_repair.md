---
title: "no boot after bad superblock repair"
date: 2011-03-12
forum: General Help
---

### Post by justjustin on 2011-03-12
Hi, I am still unable to boot after repairing a bad superblock on a partition. 
I get past grub but I get an error message about unable to read from /lib/udev. There seems to be a problem with my / partition on sda2.

From a live usb, fsck tells me all partitions are clean:
```

$ sudo fsck -v /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda1: clean, 238/269280 files, 84311/538146 blocks
$ sudo fsck -v /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda2: clean, 185808/1921360 files, 1203521/7679070 blocks
$ sudo fsck -v /dev/sda3
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda3: clean, 15845/58458112 files, 5112653/233818042 blocks

```

Boot Info Script 0.55
```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=2d03336a-1546-4a50-a736-c5d8298fe959 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=dc4a11dc-cdb8-4c13-86fd-0f8a973b9cf3 /boot           ext2    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=e66acfd5-87fa-4acb-93ef-6d0044ff10f5 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=afd1af5b-55d9-41eb-8d47-bf8486a584e5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

/dev/sda2: clean, 185808/1921360 files, 1203521/7679070 blocks

sda2:
    File system:       ext4
    Boot sector type:  Unknown

# / was on /dev/sda2 during installation
 /               ext4    errors=remount-ro 0       1

Any help much appreciated.

---

