---
title: "Recover Data from RAID 1 where Partition Table has been deleted"
date: 2010-01-12
forum: General Help
---

### Post by buck2825 on 2010-01-12
I have 8.04 running mdadm raid 1.  I selected the wrong drive in gparted and managed to hose my partition tables.  I need help please.

---

### Post by falconindy on 2010-01-12
Install/run testdisk and see if it can recreate the partition tables for you.

---

### Post by buck2825 on 2010-01-13
clarification....

/dev/sdc1 was once part of /dev/md0  I want the data off this drive.  ideally I want to simply mount /dev/sdc1

user@pc:~$ sudo mount /dev/sdc1 /test/folder
mount: you must specify the filesystem type

user@pc:~$ sudo mount -t ext3 /dev/sdc1 /test/folder
mount:wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so

I also found a thread that mentioned using
user@pc:~$ sudo mount /dev/sdc1 /test/folder -oro -text3
mount:wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so

---

### Post by falconindy on 2010-01-13
That's fine that it was part of a RAID 1 array. The fact that its RAID 1 means both disks were identical. With only a small amount of finagling, you can remove a drive from a mirrored array and use it on its own.

Testdisk is a still valid option. You might also try mounting with the with an offset of 512 bytes (past the partition table), since that's where the start of the first partition is supposed to be. Something like...

```
mount -t ext3 /dev/sdc /test/folder -o offset=512,ro
```
I'm not sure if you need the device number on the end of sdc because you're describing the device to mount via the offset, but you **certainly** want to mount as read only (ro) to protect your data.

---

### Post by buck2825 on 2010-01-13
user@PC:~$ sudo fdisk -l

Disk /dev/sda: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19fc19fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2291    18402426   83  Linux
/dev/sda2            2292        2534     1951897+  82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005ba47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001   83  Linux


user@PC:~$ sudo mount -t ext3 /dev/sdc1 /home/user/Desktop/test/ -o offset=512,ro
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@PC:~$ sudo mount -t ext3 /dev/sdc /home/user/Desktop/test/ -o offset=512,ro
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by falconindy on 2010-01-13
Ahhh my mistake -- the offset option only works with loopbacks. If the drive weren't so big you could image the entire thing and then try and mount it as a loopback...

I still vote for testdisk ;)

---

### Post by buck2825 on 2010-01-14
I took you advice and tried testdisk.  I'm not sure if it is just not working or if I'm doing something wrong.  after running testdisk, all efforts to mount the disk result in errors the same as before.  you would happen to know of a good tutorial or help file.  the web site [http://www.cgsecurity.org](http://www.cgsecurity.org) isn't helping me much as all the tutorials are for NTFS or FAT32 not ext3.

thanks

---

### Post by buck2825 on 2010-04-17
thanks for all your help I had an offsite back up a couple months old I rolled back to that and moved on with my life

thanks again

---

