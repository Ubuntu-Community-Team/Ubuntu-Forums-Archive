---
title: "Mount ext2 error"
date: 2011-03-01
forum: General Help
---

### Post by supajason on 2011-03-01
Hello,

I am trying to make an image for my NSLU2. everything is ok until it tires to mount the the ramdisk as a ext2 filesystem:

```
./genext2fs.sh 11500 /root/Downloads/NSLU2_V23R63_GPL/romfs /root/Downloads/NSLU2_V23R63_GPL/images/ramdisk
/root/Downloads/NSLU2_V23R63_GPL/images/ramdisk is not a block special device.
Proceed anyway? (y,n) mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

tail: cannot open `+2' for reading: No such file or directory
umount: /mnt/dongle: not mounted
make[1]: *** [image] Error 1
make[1]: Leaving directory `/root/Downloads/NSLU2_V23R63_GPL/vendors/Intel/IXDP425'
make: *** [image] Error 2

```here is the dmesg tail output:
```
[  922.344162] VFS: Can't find an ext2 filesystem on dev loop0.
[  952.192418] VFS: Can't find ext3 filesystem on dev loop0.
[  982.725869] VFS: Can't find ext3 filesystem on dev loop0.
[ 1094.348998] VFS: Can't find an ext2 filesystem on dev loop0.
[ 1172.509116] VFS: Can't find an ext2 filesystem on dev loop0.
[ 1492.252161] VFS: Can't find an ext2 filesystem on dev loop0.

```this is genext2fs.sh
```
#!/bin/sh

if [ $# -ne 3 ]
then
    echo "Usage: $0 size source dest"
    exit 1
fi
MNTPOINT=/mnt/dongle
mkdir -p $MNTPOINT

dd if=/dev/zero of=$3 bs=1k count=$1 2> /dev/null
echo y | /sbin/mke2fs -m 1 -q $3 $1 &> /dev/null

mkdir -p $MNTPOINT

mount -o loop -t ext2 $3 $MNTPOINT

(cd $2; find . | cpio --quiet -pud $MNTPOINT)

df $MNTPOINT | tail +2
umount $MNTPOINT
#gzip -9 < $IMG1DIR/$IMAGE.nogz > $IMG1DIR/$IMAGE
```Thank you so much for any help

---

