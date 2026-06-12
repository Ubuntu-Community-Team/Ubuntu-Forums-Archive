---
title: "/etc/fstab"
date: 2010-11-30
forum: General Help
---

### Post by domzz on 2010-11-30
Hi, I accidently rsync the whole ubuntu from one server to another :( 

I am trying to fix fstab, I think I modified it to the way it was suppose to be, but when I type fdisk -l, I get an error. I'm a total noob when it comes to fstab (or partition in general).



My fstab is:
```

/dev/md1       /       ext4     errors=remount-ro       0       1
/dev/md2       /home   ext4     errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0                1       2
/dev/sda3       swap    swap    defaults                0       0
/dev/sdb3       swap    swap    defaults        0       0
proc            /proc   proc    defaults                0       0
sysfs           /sys    sysfs   defaults                0       0
dev             /dev    devtmpfs        rw      0       0


                                                                                          
```

My df is:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
rootfs                10403064   1272824   8605956  13% /
/dev/root             10403064   1272836   8605944  13% /
/dev                   6157716       188   6157528   1% /dev
none                   6158052         0   6158052   0% /dev/shm
none                   6158052        92   6157960   1% /var/run
none                   6158052         0   6158052   0% /var/lock
/dev/md2             1442666216 437285700 932674372  32% /home   
```



When I type "sudo fdisk -l", I get

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000bea9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10485760+  fd  Linux RAID autodetect
/dev/sda2            1306      182336  1454123008   fd  Linux RAID autodetect
/dev/sda3          182336      182401      526240   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005bdaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1306    10485760+  fd  Linux RAID autodetect
/dev/sdb2            1306      182336  1454123008   fd  Linux RAID autodetect
/dev/sdb3          182336      182401      526240   82  Linux swap / Solaris

Disk /dev/md2: 1489.0 GB, 1489021894656 bytes
2 heads, 4 sectors/track, 363530736 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 10.7 GB, 10737352704 bytes
2 heads, 4 sectors/track, 2621424 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table         
```

---

### Post by shadow_code on 2010-11-30
Forgive me if I have no idea what I'm talking about :)

But it looks like md1 and md2 are being treated as disks (when they should be partitions). I'm not sure why that is, but it might hopefully give you a bit of direction :)

---

