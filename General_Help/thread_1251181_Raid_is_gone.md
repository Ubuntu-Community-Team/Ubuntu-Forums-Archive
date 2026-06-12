---
title: "Raid is gone"
date: 2009-08-27
forum: General Help
---

### Post by vakuum on 2009-08-27
Hey, 

I've just migrated from Gentoo 2008 to xubuntu 9.04. Sadly, during this migration my raid is nowhere to be found. 

I had a raid setup on sdb,sdc,sdd with lvm on it. Now there's no superblock on either of the discs. I've never seen anything like this. 

And of course, this is where I backuped my data I wanted between the move. D'oh indeed. 

root@home:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>

root@home:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d975e29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf280f280

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table


This is what is says for sdb,sdc,sdd. 
root@home:~# mdadm -D /dev/sdb
mdadm: /dev/sdb does not appear to be an md device


So what has happened here? I really like my raid back, in a working kind of way with the data on it. 

Appreciate all help..

---

### Post by tgrimley on 2009-08-27
I think you should be doing mdadm -E /dev/sdb rather than -D

what does that say?

---

### Post by vakuum on 2009-08-29
root@home:~# mdadm -E /dev/sdb
mdadm: No md superblock detected on /dev/sdb.
root@home:~# mdadm -E /dev/sdc
mdadm: No md superblock detected on /dev/sdc.
root@home:~# mdadm -E /dev/sdd
mdadm: No md superblock detected on /dev/sdd.

I also took a look at post #6 at [http://ubuntuforums.org/showthread.php?t=1101748](http://ubuntuforums.org/showthread.php?t=1101748) but I'm not sure if it's safe to continue as I'm not sure if it will break things as I'm not sure of the order in there. 

root@home:~# mdadm --create /dev/md0 --raid-devices=4 --level=5 /dev/sdb /dev/sdd missing
mdadm: You haven't given enough devices (real or missing) to create this array
root@home:~# mdadm --create /dev/md0 --raid-devices=3 --level=5 /dev/sdb /dev/sdd missing
mdadm: /dev/sdb appears to contain an ext2fs file system
    size=897079044K  mtime=Fri Mar 29 16:54:21 1974
mdadm: /dev/sdd appears to contain an ext2fs file system
    size=976770816K  mtime=Wed Aug 19 12:13:48 2009
Continue creating array? no
mdadm: create aborted.

root@home:/# mount /dev/sdb /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
root@home:/# mount /dev/sdc /mnt/
mount: you must specify the filesystem type
root@home:/# mount /dev/sdd /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/sdd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I also checked dmesg which returns: 

[176275.044667] VFS: Can't find ext4 filesystem on dev sdc.
[176278.041529] EXT3-fs error (device sdd): ext3_check_descriptors: Block bitmap for group 1920 not in group (block 197132288)!
[176278.048152] EXT3-fs: group descriptors corrupted!
[176291.110503] EXT4-fs warning (device sdb): ext4_fill_super: extents feature not enabled on this filesystem, use tune2fs.
[176291.110507] 
[176291.110508] EXT4-fs: sdb: couldn't mount because of unsupported optional features (3d18000).
[176805.832139] EXT2-fs error (device sdd): ext2_check_descriptors: Block bitmap for group 1920 not in group (block 197132288)!
[176805.832145] EXT2-fs: group descriptors corrupted!
[176808.880564] VFS: Can't find an ext2 filesystem on dev sdc.
[176815.432668] EXT2-fs error (device sdd): ext2_check_descriptors: Block bitmap for group 1920 not in group (block 197132288)!
[176815.432673] EXT2-fs: group descriptors corrupted!
[176818.941325] EXT2-fs: sdb: couldn't mount because of unsupported optional features (3d18000).
[177963.065642] VFS: Can't find ext4 filesystem on dev sdc.
[177965.177204] EXT3-fs error (device sdd): ext3_check_descriptors: Block bitmap for group 1920 not in group (block 197132288)!
[177965.192738] EXT3-fs: group descriptors corrupted!

---

### Post by vakuum on 2009-08-31
Ok, I followed [http://ubuntuforums.org/showthread.php?t=1101748](http://ubuntuforums.org/showthread.php?t=1101748) and my issue is solved! :D

---

