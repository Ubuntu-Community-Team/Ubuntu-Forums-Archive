---
title: "create custom iso and install to usb stick from shell"
date: 2012-05-14
forum: General Help
---

### Post by dstefaniuk on 2012-05-14
I'm unable to install customized Ubuntu ISO image to a USB stick. The shell script I use looks as follows:

```
ISO1=~/ubuntu-12.04-server-amd64.iso
mkdir /mnt/ubuntu > /dev/null 2>&1
umount /mnt/ubuntu > /dev/null 2>&1
mount -o loop $ISO1 /mnt/ubuntu
rm -rf ~/ubuntu
rsync -av /mnt/ubuntu/ ~/ubuntu
ISO2=~/custom.iso
mkisofs -r -V "Custom Install CD" \
    -cache-inodes \
    -J -l -b isolinux/isolinux.bin \
    -c isolinux/boot.cat -no-emul-boot \
    -boot-load-size 4 -boot-info-table \
    -o $ISO2 ~/ubuntu
dd if=$ISO2 of=/dev/sdb bs=1M
fdisk -l
```

and that produces the output:

```
# mkisofs >>>
...
Total translation table size: 2048
Total rockridge attributes bytes: 367970
Total directory bytes: 1904522
Path table size(bytes): 15792
Max brk space used 36a000
350884 extents written (685 MB)

# fdisk >>>
...
Disk /dev/sdb: 7946 MB, 7946108928 bytes
245 heads, 62 sectors/track, 1021 cylinders, total 15519744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

The ISO image ~/custom.iso created by the mkisofs command works just fine. I'm able to boot and install operating system using this image. But USB stick dosen't.

I tested the original ISO image:

```
ISO1=~/ubuntu-12.04-server-amd64.iso
dd if=$ISO1 of=/dev/sdb bs=1M
fdisk -l
```

that produces the output:

```
# fdisk >>>
...
Disk /dev/sdb: 7946 MB, 7946108928 bytes
19 heads, 24 sectors/track, 34034 cylinders, total 15519744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b5332bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     1401431      700684   17  Hidden HPFS/NTFS
```

This does work as expected - boots and installs without any problems from USB stick. So, my question is how can I create a customized Ubuntu image from shell that can be transferred properly to a USB stick?

---

### Post by dstefaniuk on 2012-05-16
In the above example mkisofs did not create a valid partition table. Using xorriso command with -isohybrid-mbr solves the problem.

```
xorriso -as mkisofs \
    -D -r -J -joliet-long -l -V "Custom Install CD" \
    -b isolinux/isolinux.bin \
    -c isolinux/boot.cat \
    -iso-level 3 -no-emul-boot -partition_offset 16 -boot-load-size 4 -boot-info-table \
    -isohybrid-mbr /usr/lib/syslinux/isohdpfx.bin \
    -o $ISO2 ~/ubuntu
```

---

