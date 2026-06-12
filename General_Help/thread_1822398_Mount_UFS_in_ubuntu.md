---
title: "Mount UFS in ubuntu"
date: 2011-08-10
forum: General Help
---

### Post by tadcan on 2011-08-10
I tried to follow this guide to mount a UFS disk in ubuntu. Its from a sony DVD player and tv recorder so I don't have much info about it.

[http://www.sysadmindiary.com/2008/03/mounting-freebsd-ufs2-file-system-on-ubuntu-linux/](http://www.sysadmindiary.com/2008/03/mounting-freebsd-ufs2-file-system-on-ubuntu-linux/)

```
dmesg |grep "bsd:"
```
This just brings a new line and doesn't give the output in the article

```
sudo mkdir /mnt/ufsdisk
```
This works
```
sudo mount -t ufs -r -o ufstype=ufs2 /dev/sda5 /mnt/ufsdisk

```
That give the following
```
mount: /dev/sda5 already mounted or /mnt/ufsdisk busy
mount: according to mtab, /dev/sda5 is mounted on /

```
This next command ```
mount
``` gives this
```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
cgroup on /dev/cgroup/cpu type cgroup (rw,cpu)
/dev/sdd1 on /media/702A-9012 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```

Any advice

---

### Post by karlson on 2011-08-10
> **tadcan said:**
> I tried to follow this guide to mount a UFS disk in ubuntu. Its from a sony DVD player and tv recorder so I don't have much info about it.

[http://www.sysadmindiary.com/2008/03/mounting-freebsd-ufs2-file-system-on-ubuntu-linux/](http://www.sysadmindiary.com/2008/03/mounting-freebsd-ufs2-file-system-on-ubuntu-linux/)

```
dmesg |grep "bsd:"
```
This just brings a new line and doesn't give the output in the article

```
sudo mkdir /mnt/ufsdisk
```
This works
```
sudo mount -t ufs -r -o ufstype=ufs2 /dev/sda5 /mnt/ufsdisk

```
That give the following
```
mount: /dev/sda5 already mounted or /mnt/ufsdisk busy
mount: according to mtab, /dev/sda5 is mounted on /

```
This next command ```
mount
``` gives this
```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
cgroup on /dev/cgroup/cpu type cgroup (rw,cpu)
/dev/sdd1 on /media/702A-9012 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```

Any advice

Can you include output of
```

$ sudo df -k
$ sudo fdisk -l

```

---

### Post by tadcan on 2011-08-10
sudo df -k
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             76503804  15109916  57507552  21% /
none                   1667044       780   1666264   1% /dev
none                   1676632      1620   1675012   1% /dev/shm
none                   1676632       364   1676268   1% /var/run
none                   1676632         0   1676632   0% /var/lock
/dev/sdd1              3862528   3085024    777504  80% /media/702A-9012

```


sudo fdisk -l
```
Disk /dev/sda: 750.2 GB, 750155292160 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1f136f4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       70045   562533038+   7  HPFS/NTFS
/dev/sda3           70046       81003    88015872    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           81003       91202    81918977    5  Extended
/dev/sda5           81003       90680    77726720   83  Linux
/dev/sda6           90680       91202     4191232   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
256 heads, 63 sectors/track, 19381 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcbaeef6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19382   156290902   a5  FreeBSD

Disk /dev/sdc: 1500.3 GB, 1500300828160 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4870980

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdd: 3963 MB, 3963617280 bytes
128 heads, 63 sectors/track, 960 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc79588ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1 
```

---

