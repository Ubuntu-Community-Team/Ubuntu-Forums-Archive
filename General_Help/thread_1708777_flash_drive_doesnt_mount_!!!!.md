---
title: "flash drive doesnt mount !!!!"
date: 2011-03-17
forum: General Help
---

### Post by vivek.pandey on 2011-03-17
hey everyone 
   i bought i 32gb transcend flashdrive mainly to t0 another os.. but the problem is it doesnt mount in ubuntu 10.10 but is mounts in windows. when i type lsusb in my terminal after inserting ang again after removing it i see that there is one usb device which is shown when flash drive is inserted and dissapears when i remove my flash drive

can anybody please help
thanx to aLL

---

### Post by ~Hinterland on 2011-03-17
You probably just need to unmount properly in windows, you can right click on the USB icon and 'Safely Remove Hardware'(if I remember right.

---

### Post by vivek.pandey on 2011-03-17
> **~Hinterland said:**
> You probably just need to unmount properly in windows, you can right click on the USB icon and 'Safely Remove Hardware'(if I remember right.

thanx for your quick reply
I first inserted my flash drive in ubuntu so i guess no question of unmounting

---

### Post by vivek.pandey on 2011-03-17
ok new status . i cant format my flash drive now in windows, actually from the starting itself..is it corrupted?

---

### Post by vivek.pandey on 2011-03-17
anyone?

---

### Post by vivek.pandey on 2011-03-18
please someone help me :-(

---

### Post by arun ganesh on 2011-03-18
perhaps...i too faced the same problem,,,,,try recuva which is used for recovery....First try in windows..

Also check in Ubuntu 10.10 whether pendrive is mounted or not
type cd /dev
check for your pendrive name....

---

### Post by 5149.5 on 2011-03-18
Here is a link for setting up automounting.
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by vivek.pandey on 2011-03-18
> **arun ganesh said:**
> perhaps...i too faced the same problem,,,,,try recuva which is used for recovery....First try in windows..

Also check in Ubuntu 10.10 whether pendrive is mounted or not
type cd /dev
check for your pendrive name....

ok if you too faced the same problem then how did you fix it?

---

### Post by vivek.pandey on 2011-03-18
hey everyone i followed this link
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
when i type sudo fdisk -l i get following result
```
vivek@NEO:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          49      393561   de  Dell Utility
/dev/sda2              50        1240     9565184    7  HPFS/NTFS
/dev/sda3   *        1241       23295   177150976    7  HPFS/NTFS
/dev/sda4           23295       38914   125458433    f  W95 Ext'd (LBA)
/dev/sda5           23295       28497    41783183    7  HPFS/NTFS
/dev/sda6           28497       33423    39569408   83  Linux
/dev/sda7           33423       33639     1738752   82  Linux swap / Solaris
/dev/sda8           33640       38692    40577024   83  Linux
/dev/sda9           38692       38914     1780736   82  Linux swap / Solaris

Disk /dev/sdc: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0626e280

Disk /dev/sdc doesn't contain a valid partition table

i guess /dev/sdc is my flash drive 

vivek@NEO:~$ sudo mkdir /media/external
vivek@NEO:~$ sudo mount -t vfat /dev/sdc /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
i tried with ntfs also i get
```

vivek@NEO:~$ sudo mount -t ntfs /dev/sdc /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

now any idea wats wrong ? thanx to all

---

### Post by vivek.pandey on 2011-03-19
updates .. k i guess /dev/sdc is not for the flash drive...i enabled automount and i got this error when i inserted the flash drive

Error mounting: mount: /dev/sdd: can't read superblock

dont know whats going on?

/dev/sda7           33423       33639     1738752   82  Linux swap / Solaris

and where from solaris has come?
i am not using solaris os... i just have mac theme... is it making this solaris part..pls help someone... i am freaking out now with this flash drive problem

---

### Post by vivek.pandey on 2011-03-21
can no one solve this problem?

---

