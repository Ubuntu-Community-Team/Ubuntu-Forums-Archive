---
title: "gparted - attempted resize/move of ext3 partion fail"
date: 2011-01-01
forum: General Help
---

### Post by ktat on 2011-01-01
Hi All,

I could really use some help here, I have made my /home partition inaccessible :(

Problem started when I used gparted to resize and move /dev/sda3 (where all my personal data is).  This partition is about 250G and the process was going to take some hours to complete so I went to bed before it finished.  When I checked it in the morning my pc had shut itself down, so I rebooted and started up gparted again.  Looking at the partition table in gparted I noticed that /dev/sda6 had been resized, however it hadn't been moved.  I tried to move it and the following error came up...



```
GParted 0.5.2
Libparted 2.2
Check and repair file system (ext3) on /dev/sda3  00:00:01    ( ERROR )
calibrate /dev/sda3  00:00:01    ( SUCCESS )
path: /dev/sda3
start: 39054829
end: 474914343
size: 435859515 (207.83 GiB)
check file system on /dev/sda3 for errors and (if possible) fix them  00:00:00    ( ERROR )
e2fsck -f -y -v /dev/sda3
e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: going back to original superblock
Filesystem mounted or opened exclusively by another program?
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: The ext2 superblock is corrupt when using the backup blocks
e2fsck: Device or resource busy while trying to open /dev/sda3
```

I then did some research and tried to fix the problem from the commandline...

```
karlos@ubuntu-10:~$ sudo resize2fs -Mp /dev/sda3
resize2fs 1.41.11 (14-Mar-2010)
Please run 'e2fsck -f /dev/sda3' first.

karlos@ubuntu-10:~$ fc 377
sudo resize2fs -Mpf /dev/sda3
resize2fs 1.41.11 (14-Mar-2010)
Resizing the filesystem on /dev/sda3 to 36415183 (4k) blocks.
resize2fs: A block group is missing an inode table while trying to resize /dev/sda3
Please run 'e2fsck -fy /dev/sda3' to fix the filesystem
after the aborted resize operation.

karlos@ubuntu-10:~$ sudo e2fsck -f /dev/sda3
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: The ext2 superblock is corrupt when using the backup blocks
e2fsck: going back to original superblock
e2fsck: Device or resource busy while trying to open /dev/sda3
Filesystem mounted or opened exclusively by another program?

karlos@ubuntu-10:~$ sudo e2fsck -fy /dev/sda3
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: The ext2 superblock is corrupt when using the backup blocks
e2fsck: going back to original superblock
e2fsck: Device or resource busy while trying to open /dev/sda3
Filesystem mounted or opened exclusively by another program?
```

I then tried to use backup superblocks at 8193, 16384, 32768...

```
karlos@ubuntu-10:~$ sudo e2fsck -fy -b 32768 /dev/sda3
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sda3
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
I really can't see that it is mounted at all...
```
karlos@ubuntu-10:~$ mount -l -t ext3
/dev/sdc1 on / type ext3 (rw,errors=remount-ro)
/dev/sdb1 on /home/karlos/backup type ext3 (rw) [backup]
/dev/sda6 on /media/SUSE type ext3 (rw,nosuid,nodev,uhelper=udisks) [SUSE]
```

This is the dmesg output...

```
karlos@ubuntu-10:~$ dmesg|tail
[ 4588.270555] EXT3 FS on sda6, internal journal
[ 4588.270565] EXT3-fs: mounted filesystem with ordered data mode.
[ 4669.197392] kjournald starting.  Commit interval 5 seconds
[ 4669.197633] EXT3 FS on sda6, internal journal
[ 4669.197643] EXT3-fs: mounted filesystem with ordered data mode.
[ 6401.853257] kjournald starting.  Commit interval 5 seconds
[ 6401.853573] EXT3 FS on sda6, internal journal
[ 6401.853584] EXT3-fs: mounted filesystem with ordered data mode.
[ 7895.924569] EXT3-fs error (device sda3): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 7895.925081] EXT3-fs: group descriptors corrupted!
```



There must be some way to restore access to this partion? Can anyone please help me, I am happy to do more research and teach myself - but I need to be pointed in the right direction, thanks :)

---

