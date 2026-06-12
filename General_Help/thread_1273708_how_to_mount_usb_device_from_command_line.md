---
title: "how to mount usb device from command line"
date: 2009-09-23
forum: General Help
---

### Post by blur xc on 2009-09-23
I know how to mount devices of which I already know their names (sda2, sdb1, etc..., or by UUID numbers), but how do you know the name of a usb device you might want to mount from the command line?  I've got a mutli card reader, and I have no idea what the names are of the different "slots", or even the usb ports on my box.  If it weren't for nautilus and the gui- I'd be lost.

Thanks,
BM

---

### Post by Peacefulpieofdeath on 2009-09-23
sorry i read wrong, look into gparted when its pluged to see the sda(?).

---

### Post by jerrrys on 2009-09-23
in 8.04 i simply have to enter **lsusb**

---

### Post by ajgreeny on 2009-09-23
For a usb disk or storage use sudo fdisk -l and you will get an output like this
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd44cd44c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2823    22675716    7  HPFS/NTFS
/dev/sda2            2824       19777   136183005   83  Linux
/dev/sda4           19778       19929     1220940    5  Extended
/dev/sda5           19778       19929     1220908+  82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62c86a43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2453    19703691   83  Linux
/dev/sdb2            2454        4998    20442712+  83  Linux
```
You should be able to work out the /dev/sdx# from that for the disk in question and use that in the mount command.

---

### Post by blur xc on 2009-09-26
Ok, I'm getting it figured out now.  One more question, do flash drives, memory cards, etc., have a uuid number?  When I run blkid, I get uuid's for all my hard disks, but nothing for the flash drives.  

Also, when ubuntu automounts a disk, I notice that it creates a direcotry, ie. /mount/disk to mount the flash drive.  But when I want to mount it manually, I need to first sudo mkdir /mount/disk, then mount to that location.  So, when you unmount in Ubuntu, does it automatically remove the /mount/disk directory?

Also, according to the book I'm reading, they say to use mount with the -t option, and specify the file-system type.  What if you don't know the filesystem type?  What happens if you enter the wrong file-system type by mistake?  I've been leaving that option out and just entering mount /dev/sdg1 /media/disk.  It seems Linux can figure out hte file-system type all by itself.

Thanks,
BM

---

### Post by ajgreeny on 2009-09-26
Yes they do , and here's the output from my machine to prove it.

> /dev/sda1: UUID="00947AAF947AA6B6" LABEL="WindowsXP" TYPE="ntfs" 
/dev/sda2: UUID="7a49a256-2471-45cc-9933-78b8a5bbcfe9" TYPE="ext3" LABEL="Ubuntu904" 
/dev/sda5: TYPE="swap" UUID="1bfd912d-b6b6-4a68-9aaf-4139513772ec" 
/dev/sdb1: LABEL="Mint7" UUID="a9f2c0ca-dad3-4617-b5a1-0fad9db95d2e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: LABEL="Jaunty904" UUID="10ec6342-7b3f-425c-8655-c637bb65ae72" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="KINGSTON512" UUID="4883-BAC7" TYPE="vfat"

I have no idea why your's does not appear to have a UUID, but note how short mine is compared to the hard disk partitions.  Maybe something to do with vfat filesystem, perhaps the reason is that the disk has a label, or perhaps the small size, or maybe something else but whatever it is, I'm afraid I don't know the answer to your question.

---

