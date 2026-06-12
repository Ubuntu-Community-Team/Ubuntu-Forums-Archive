---
title: "unable to mount/unmount  in ubuntu 10.04"
date: 2010-05-07
forum: General Help
---

### Post by bilol on 2010-05-07
Hi all,

I am unable to mount partition in ubuntu 10.04. Icons for different partitions are not coming within "Places".Every time I have to manually mount the partition or CD or DVD and manually unmount it.
Seldom it shows the partition icons within Places>Computer. Then the partitions are getting mounted upon double clicking its partition-icon. But I fail to unmount the partition as it throws the error* "media/partition_name  is not in the fstab (and you are not root)."*
**Need your help....**..

---

### Post by darolu on 2010-05-07
Open a terminal (Applications -Accessories - Terminal) and run these commands:
```
$ sudo fdisk -l
```
And post your results, then:
```
$ cat /etc/fstab
```
And post the results.

This information will help us to determine what is wrong.

---

### Post by rnerwein on 2010-05-07
hi
are you member of the following groups ( grep our_username /etc/group )

adm dialout fax cdrom floppy tape audio dip video plugdev fuse lpadmin
netdev admin sambashare

and -- how does your /etc/fstab looks like ?
did you made a fresh install or upgrade ?
ciao

---

### Post by bilol on 2010-05-07
I have done a fresh install of ubuntu 10.04 and this problem was not existing in ubuntu 9.10. 
Sorry,right now I can not post you the output you wanted, because the concerned PC is in my home and now I am in office.

---

### Post by bilol on 2010-05-07
This is the intended output :

```
dhiman@dhiman-desktop:~$ **sudo fdisk -l**
[sudo] password for dhiman: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1ce41ce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda3            1276       14593   106976225+   f  W95 Ext'd (LBA)
/dev/sda5            3887       10413    52428096    7  HPFS/NTFS
/dev/sda6           10414       12371    15727603+   7  HPFS/NTFS
/dev/sda7           12372       14593    17848183+   7  HPFS/NTFS
/dev/sda8            1276        1400      999424   82  Linux swap / Solaris
/dev/sda9            1400        3886    19971072   83  Linux

Partition table entries are not in disk order



**dhiman@dhiman-desktop:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=cd34f818-a3e1-4db9-93e8-375e8106008d /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d12e0cc4-9c14-49c6-85dd-769f10faf652 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



**dhiman@dhiman-desktop:~$ grep dhiman /etc/group**
adm:x:4:dhiman
dialout:x:20:dhiman
cdrom:x:24:dhiman
plugdev:x:46:dhiman
lpadmin:x:105:dhiman
admin:x:119:dhiman
dhiman:x:1000:
sambashare:x:122:dhiman
```

---

### Post by bilol on 2010-05-10
need your help...urgent

---

### Post by bilol on 2010-05-12
can anybody send some suggestion !!!!!!!!!

---

### Post by rnerwein on 2010-05-12
hi
yeah your fstab is looking strange. all the windows stuff is missing. why ? i don't now.
but follow those steps.
1. sudo mkdir /win01 /win02 /win03 /win04   ( or name that mount points as you want ).
2. insert into your /etc/fstab  ( use your prefered editor for that ).
/dev/sdc1 /win01 ntfs defaults umask=000 0 0
/dev/sdc5 /win05 ntfs defaults umask=000 0 0
/dev/sdc6 /win06 ntfs defaults umask=000 0 0
/dev/sdc7 /win07 ntfs defaults umask=000 0 0
save the file
test your entries: sudo mount -a ( or mountall )
have a look if your entries where mounted: mount
if every thing is ok the filesystems will be mounted on every boot.
have fun
ciao

---

### Post by bilol on 2010-05-12
thanks a lot rnerwein....
to auto-mount my flash drive (FAT 32) what similar lines to be added in fstab?

---

### Post by bilol on 2010-05-13
> your fstab is looking strange. all the windows stuff is missing. why ?
I don't think fstab need to have all info regarding different windows stuff.
In another Lynx-installed desktop( my office PC) there is no problem in auto-mount.Let me show you its fstab:

```
dhiman@dhiman-desktop:~$ **sudo cat /etc/fstab**
[sudo] password for dhiman: 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext2    errors=remount-ro 0       1
/dev/sda8       none            swap    sw              0       0


dhiman@dhiman-desktop:~$ **sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19451   125523230+   f  W95 Ext'd (LBA)
/dev/sda5            7904       12365    35840983+   7  HPFS/NTFS
/dev/sda6           12366       19451    56918263+   7  HPFS/NTFS
/dev/sda7            4323        7903    28763136   83  Linux
/dev/sda8            3825        4322     3998720   82  Linux swap / Solaris

Partition table entries are not in disk order
 
```

---

