---
title: "USB thumb-drive (fat32) read only"
date: 2010-08-18
forum: General Help
---

### Post by ahalin on 2010-08-18
My FAT32 USB pen-drive has recently become read only (again), in Ubuntu, Ubuntu NBR and Xubuntu 10.04. The pen-drive mounts and files can be copied from it. Windows can still read/write to it. I have tried most of the usual tricks (see below) less doing yet another reformat, which I want to avoid. 

One clue may be a number of files tucked away in a sub-folder. They have names like “÷«~&#9496;)·&#8976;.&#9560;Nº” and “b&#9492;g&#8992;m-i½.&#9580;&#9574;&#9574;” and were modified in 1901 or 1947!!! They are listed as executable programs in their properties (“Allow executing as a program file") and their file size is over 10 Gb, which is funny given that the pen-drive is only 2 Gb!!! I assume they are viruses and will try and clean them in Windows.

If I cd to the relevant directory and try to remove the offending folder:
```
$ rm Monthly
```
```
rm: cannot remove `Monthly': Read-only file system
```

or even 
```
$ rm -rf Monthly
```
```
rm: cannot remove `Monthly/\  *(list of files)*': Read-only file system
```

OK, is it read write?
```
$ mount
```
```
/dev/sdf1 on /media/My2GBusb type vfat  (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
```

Looks like it but lets chown:
```
$ sudo chown john:john -R /media/My2GBusb
```
```
chown: changing ownership of `/media/My2GBusb': Read-only file system
```

So it’s read only and I can’t change it. Details on the pen-drive are shown below.

```
$ dmesg
```
```
[ 1631.942438] FAT: Filesystem error (dev sdf1) [ 1631.942455] invalid access to FAT (entry 0x0bab04ad)
```

```
$ sudo parted /dev/sdf print
```
```
Model: Verbatim STORE N GO (scsi) 
Disk /dev/sdf: 2003MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size    Type     File system  Flags
1      4129kB  2003MB  1999MB  primary  fat32
```

```
$ sudo fsck /dev/sdf$
```
```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No medium found while trying to open /dev/sdf
The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device&gt;
```

```
$ sudo dosfsck -a -v /dev/sdf
```
```
dosfsck 3.0.7 (24 Dec 2009)
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
Logical sector size (7950 bytes) is not a multiple of the physical sector size.
```
So a couple of errors in there, but I haven't been able to fix them. Any suggestions?

---

### Post by dcstar on 2010-08-19
> **ahalin said:**
> 
........
```
$ sudo dosfsck -a -v /dev/sdf
```
```
dosfsck 3.0.7 (24 Dec 2009)
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
Logical sector size (7950 bytes) is not a multiple of the physical sector size.
```
So a couple of errors in there, but I haven't been able to fix them. Any suggestions?
Devices are **not** partitions:
```
sudo dosfsck -a -v /dev/sdf1
```

---

### Post by zaphod777 on 2010-08-19
none of the chown or fsck commands will work on it since it is a MS file system and fat32 has no security options anyway. 

can't you delete the offending directory's in Windows? 

you might be able to run 
```
sudo rm -r -f Monthly
```

Since it is only a 2GB thumb drive why not just copy off the 2GB of data and reformat it and copy it back? I can't imagine it would take longer to do that than to make your post. Maybe I am missing something though.

---

### Post by gifford.scott on 2010-08-24
I recently ran into a similar problem when I accidentally pulled out a VFAT-formatted USB drive w/o unmounting it.  In my case, the issue was that the USB drive now had a corrupt FAT, and when the USB drive was inserted, the Nautilus file GUI was silently marking the drive as read-only to prevent further writes to the corrupt FAT.

The fix:

With the USB drive plugged in, unmount the USB drive (right-click on the drive icon on your desktop and select 'Unmount') and bring up the GPartEd partition editor (System->Administration->GPartEd).  Under GPartEd, select the USB drive (typically, /dev/sdb) in the upper right-hand pull-down list.  If you've chosen the right drive and it's unmounted, you can right-click on any of the partitions listed (typically, only one: /dev/sdb1) and select 'Check' to perform a filesystem check on the partition.  Running a filesystem check should correct the FAT on the drive partition - just pull-out and reinsert the USB drive and it should be restored to read-write.

---

### Post by approaching on 2010-09-10
ok, I solved my problem. I hadn't found anything that worked with linux, but I ran the chkdsk utility via the windows command line to fix it and it succeeded (though it took *forever*). I don't like to admit that I was able to do something in windows that I couldn't on linux, but it's sort of because windows ****ed up it's own file system in the first place, so whatever.

---

### Post by paran0rmal on 2010-11-07
This worked for me... thanks! In my case my daughter crawled under my desk and switched off while I was doing some writes to the file system. Just one note, you can unmount it straight out of GParted, so there's no need to first unmount and then launch GParted. 

> **gifford.scott said:**
> I recently ran into a similar problem when I accidentally pulled out a VFAT-formatted USB drive w/o unmounting it.  In my case, the issue was that the USB drive now had a corrupt FAT, and when the USB drive was inserted, the Nautilus file GUI was silently marking the drive as read-only to prevent further writes to the corrupt FAT.

The fix:

With the USB drive plugged in, unmount the USB drive (right-click on the drive icon on your desktop and select 'Unmount') and bring up the GPartEd partition editor (System->Administration->GPartEd).  Under GPartEd, select the USB drive (typically, /dev/sdb) in the upper right-hand pull-down list.  If you've chosen the right drive and it's unmounted, you can right-click on any of the partitions listed (typically, only one: /dev/sdb1) and select 'Check' to perform a filesystem check on the partition.  Running a filesystem check should correct the FAT on the drive partition - just pull-out and reinsert the USB drive and it should be restored to read-write.

---

### Post by bmwerks on 2011-03-17
> **dcstar said:**
> Devices are **not** partitions:
```
sudo dosfsck -a -v /dev/sdf1
```

I had to run gparted to understand this message but it makes sense now. i was running the code with just "/dev/sdc" when i needed to include "/dev/sdc**1**"

I finally got dosfsck to run!

---

