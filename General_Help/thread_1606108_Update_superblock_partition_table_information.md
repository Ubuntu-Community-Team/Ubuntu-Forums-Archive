---
title: "Update superblock/ partition table information?"
date: 2010-10-26
forum: General Help
---

### Post by spoovy on 2010-10-26
I accidentally resized my /boot partition (thought I was resizing a flash drive partition #-o).

It still boots, but with error messages, from dmesg and /var/boot.log respectively - 

```

[   13.852109] REISERFS (device sda6): checking transaction log (sda6)
[   13.891795] REISERFS (device sda6): Using r5 hash to sort names
[   14.438293] EXT4-fs (sda9): mounted filesystem with ordered data mode
[   37.948843] EXT2-fs warning: mounting fs with errors, running e2fsck is recommended

```

```


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
mountall: fsck /boot [927] terminated with status 4
mountall: Filesystem has errors: /boot
Skipping /boot at user request

```


I tried to do as suggested, but got the following result - 

```

spoovy@poppy:~$ sudo umount /dev/sda1
spoovy@poppy:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 1903584 blocks
The physical size of the device is 200781 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 204812 (Invalid argument) while getting next inode from scan.  Ignore error<y>? no

Error while scanning inodes (102000): Can't read next inode
e2fsck: aborted
spoovy@poppy:~$ 

```Seems it won't accept the discrepancy in size.   Any ideas how to fix, anyone?

Thanks in advance

Spoov

---

