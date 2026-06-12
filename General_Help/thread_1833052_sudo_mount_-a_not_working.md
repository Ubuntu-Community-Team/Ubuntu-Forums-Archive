---
title: "sudo mount -a not working"
date: 2011-08-25
forum: General Help
---

### Post by Robbyx on 2011-08-25
I am having to reboot to mount all the partitions listed in fstab, if I had previously gone into gparted. I also have the panel app that shows each drive and if it is mounted. It gives me to option to mount the drive. I am finding the mount option  is not working. What can I do to force the drives to be mounted?  11.04

---

### Post by fdrake on 2011-08-25
> **Robbyx said:**
> I am having to reboot to mount all the partitions listed in fstab, if I had previously gone into gparted. I also have the panel app that shows each drive and if it is mounted. It gives me to option to mount the drive. I am finding the mount option  is not working. What can I do to force the drives to be mounted?  11.04
an alternative is
```

man udisks

```
post your
```
less fstab
sudo fdisk -l
```

what kinf of error does "mount -a" gives you (device is busy?)?

---

### Post by WorMzy on 2011-08-25
Make sure that gparted is fully closed before trying to mount a partition. Gparted scans and locks the disks to try and prevent any potential conflicts with mounting software: [http://gparted.sourceforge.net/faq.php#faq-12](http://gparted.sourceforge.net/faq.php#faq-12)

---

### Post by Robbyx on 2011-08-25
> **fdrake said:**
> an alternative is
```

man udisks

```
post your
```
less fstab
sudo fdisk -l
```

what kind of error does "mount -a" gives you (device is busy?)?
No error. The partitions are not mounted. It is as if I had not given the command to mount the partitions.


**fstab**
> proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b9146602-f837-4b0b-b788-61f50ef09dc0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=eff6e720-d952-4289-8e3f-2d31e0c27888 /home           ext4    defaults        0       2

# spare1 was on /dev/sda5 during installation
UUID=4ea4f26d-0c99-4918-a4ea-fcad426e97fc /media/spare1           ext4    defaults        0       2
# spare2 was on /dev/sda6 during installation
UUID=b2df1606-77d7-4ec0-a8f8-509ad75cbce5 /media/spare2           ext4    defaults        0       2
# my docs was on /dev/sda7 during installation
UUID=e53a03ef-bf3c-4d2e-80ed-58a5baadd201 /media/mydocs          ext4    defaults        0       2
# backup was on /dev/sdc6 during installation
UUID=86290d05-e673-4310-9f3e-93af30cc13af /media/audio_visual  reiserfs    defaults        0       2

# swap was on /dev/sda9 during installation
UUID=d73b54e8-63f1-463e-8f7e-cb458d614eaf none            swap    sw              0       0

**sudo fdisk -l**

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009df22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30720000   83  Linux
/dev/sda2            3825        8924    40960000   83  Linux
/dev/sda3            8925      121602   905079809    5  Extended
/dev/sda5            8925       11474    20480000   83  Linux
/dev/sda6           11474       14024    20480000   83  Linux
/dev/sda7           14024      120837   857973760   83  Linux
/dev/sda8          120837      121602     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244204033+   f  W95 Ext'd (LBA)
/dev/sdb5           25084       30401    42716803+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09f909f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdc2           25084       30401    42716835    f  W95 Ext'd (LBA)
/dev/sdc5           25084       30401    42716803+   c  W95 FAT32 (LBA)

Disk /dev/sdd: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        3725    29921031   83  Linux
/dev/sdd2            3726        7647    31503465   83  Linux
/dev/sdd3            7648       60057   420983294+   5  Extended
/dev/sdd4           60058       60801     5976180   82  Linux swap / Solaris
/dev/sdd5            7648       21000   107257941   83  Linux
/dev/sdd6           21001       60057   313725321   83  Linux

Disk /dev/sde: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3aa5e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        7840     2007024    c  W95 FAT32 (LBA)
robin@robin-EP35-DS3L:~$ 

After doing the above I went into and then existed from gparted. According to  pcman none of my partitions are mounted.

---

### Post by fdrake on 2011-08-25
what's the output of "mount"?

---

### Post by Robbyx on 2011-08-25
> **fdrake said:**
> what's the output of "mount"?

```
robin@robin-EP35-DS3L:~$ sudo mount
[sudo] password for robin: 
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdd6 on /media/audio_visual type reiserfs (rw)
/dev/sda2 on /home type ext4 (rw,commit=0)
/dev/sda6 on /media/spare2 type ext4 (rw,commit=0)
/dev/sda5 on /media/spare1 type ext4 (rw,commit=0)
/dev/sda7 on /media/mydocs type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/robin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robin)
/dev/sde1 on /media/E0D0-35DF type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
javafs on /home/robin/WualaDrive type fuse.javafs (rw,nosuid,nodev,user=robin)
/dev/sdd5 on /media/7b859c36-c68d-408f-9425-de9f525f3c71 type reiserfs (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd2 on /media/500mg Home type ext3 (rw,nosuid,nodev,uhelper=udisks)
robin@robin-EP35-DS3L:~$ 

```

---

