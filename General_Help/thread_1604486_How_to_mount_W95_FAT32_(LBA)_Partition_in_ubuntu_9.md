---
title: "How to mount W95 FAT32 (LBA) Partition in ubuntu 9.10?"
date: 2010-10-24
forum: General Help
---

### Post by srinivasareddyp on 2010-10-24
Hi guys,

I am unable to mount my "W95 FAT32(LBA)" partition in my ubuntu 9.10. 
#fdisk -l    //gives the following output
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48b9d15a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5106    41013913+   5  Extended
/dev/sda2   *        5107        9728    37126215   af  HFS / HFS+
/dev/sda3            9729       14593    39078112+   c  W95 FAT32 (LBA)
/dev/sda5               1        2550    20482812    b  W95 FAT32
/dev/sda6            4864        5106     1951866   82  Linux swap / Solaris
/dev/sda7            2551        4863    18579141    7  HPFS/NTFS

Partition table entries are not in disk order

now i want to mount my /dev/sda3 partiotion
so i tried mount as follows 

#sudo mount -t vfat /dev/sda3 /media/sda3

and im getting following output 

mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
I searched for a solution in many forums but in vain. So as a last attempt im posting it here.. hope some one can help.

Thank You
srinivas

---

### Post by Herman on 2010-10-24
:) There's nothing wrong with your mount command, I tested it in my Lucid Lynx/ Windows 98SE computer and the same command worked fine when I tried it on the W95 FAT32 (LBA) file system in my computer.

The most common reason why it can be difficult to get Ubuntu to mount a file system is that the file system needs a file system check.
Have you tried running 'scandisk' on it? You should be able to do that from within Windows, (schedule a disk check for the next reboot), or with a Windows CD or floppy disk. I think for Windows 95 your file system checker will be in your boot floppy.

If you can't get Windows to check and repair it's file system it for you, it's also possible to run a file system check on a FAT32 file system from Ubuntu, 
```
sudo fsck.vfat -a -l -v /dev/sda3
```Never run a file system check on any file system while it is mounted.

After a file system check has completed then you may try the mount command again and it should work. :)

---

### Post by srinivasareddyp on 2010-10-25
hi herman,

This is the output i got after running fsck

```
#sudo fsck.vfat -a -l -v /dev/sda3
dosfsck 3.0.3 (18 May 2009)
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
Logical sector size is zero.
```

After i tried mount and it didnt get mounted

---

### Post by efflandt on 2010-10-25
The problem might be that: **Partition table entries are not in disk order**

sda7 HPFS.HTFS should be sda6
sda6 Linux swap should be sda7.

How did that happen?  You might want to record the output of **sudo fdisk -lu**

Then from Ubuntu live CD/USB using the -lu start/end numbers use **sudo fdisk -u**
to delete sda6 and sda7 and recreate sda6 with start, end, and type 7 that sda7 had,
and make sda7 with start, end and type 82 that sda6 had.

---

### Post by Herman on 2010-10-25
> Logical sector size is zero.:confused: Should be more like: "512 bytes per logical sector".
You should have received a verbose output.

Try running the same command on some other (normal) FAT32 file system if you have one available, (like in a USB flash memory stick or floppy fdisk the or like), so you'll get an idea of what kind out feedback is normal from that command.

I'm sorry to have to tell you this, but it doesn't seem to me as if you have a proper file system in that partition. If there was it seems to have been damaged somehow, and you didn't have your files backup up then I'd say it's time to start trying out file recovery tools like photorec, (in testdisk), and so on. Just my opinion. 

Partitions can be numbered in any order. :)

---

