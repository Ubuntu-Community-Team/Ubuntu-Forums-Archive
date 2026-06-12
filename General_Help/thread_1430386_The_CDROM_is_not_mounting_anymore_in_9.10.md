---
title: "The CDROM is not mounting anymore in 9.10"
date: 2010-03-15
forum: General Help
---

### Post by franciskus on 2010-03-15
I need help to know what can I do fix this problem.

I have Ubuntu 9.10, the cdrom was mounting normally, suddenly it stopped mounting and now when I insert a CD/DVD nothing happens.

My fstab is like this:
[FONT="Courier New"]/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 [/FONT]

When I run **hwinfo --cdrom** it says:
```
francisco@francisco-desktop:~$ hwinfo --cdrom
18: SCSI 300.0: 10602 CD-ROM (DVD)                              
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_CDDVDW_SH_S223F
  Unique ID: KD9E.+o0IDY85DU5
  Parent ID: w7Y8.tBwwt1mPXq2
  SysFS ID: /class/block/sr0
  SysFS BusID: 3:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host3/target3:0:0/3:0:0:0
  Hardware Class: cdrom
  Model: "TSSTcorp CDDVDW SH-S223F"
  Vendor: "TSSTcorp"
  Device: "CDDVDW SH-S223F"
  Revision: "SB02"
  Driver: "ata_piix", "sr"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (IDE interface)
  Drive Speed: 48

```

When I insert a CD/DVD and I try to mount it in the command line I get this:
```
francisco@francisco-desktop:~$ sudo mount /dev/sr0 /media/cdrom0
mount: /dev/sr0: dispositivo de blocos desconhecido
francisco@francisco-desktop:~$ 

```
It is in Portuguese but it means "**Unknown blocks device**".

Could anyone please help me on this?

---

### Post by km0r3 on 2010-03-15
This happened after installing Ubuntu 9.10 or *using *Ubuntu after a while and *then* this occurred?

Please be more descriptive :) . I cannot read anything suspicious from your information.

---

### Post by franciskus on 2010-03-15
I know, the problem is totally weird, when I installed 9.10 it was mounting then after days using it started not mounting anymore, it starts to read the CD (the green light blinks) but nothing else happen.

Thanks for helping, I tried to specify as much as I could.

---

### Post by franciskus on 2010-03-16
I just found out that my file **sr0** in **/dev/** directory is totally empty, **0 bytes**.

The owner is **root** and the group is **cdrom**

Shouldn't have something in this file **sr0** since?
```
francisco@francisco-desktop:~$ ls -l /dev/ | grep cd
lrwxrwxrwx  1 root root           3 2010-03-16 18:44 cdrom -> sr0
lrwxrwxrwx  1 root root           3 2010-03-16 18:44 cdrw -> sr0
drwxr-xr-x  2 root root          60 2010-03-16 18:44 pktcdvd
lrwxrwxrwx  1 root root           3 2010-03-16 18:44 scd0 -> sr0
crw-rw----  1 root cdrom    21,   1 2010-03-16 18:44 sg1
brw-rw----+ 1 root cdrom    11,   0 2010-03-16 18:44 sr0
francisco@francisco-desktop:~$ ls -l /dev/cdr* 
lrwxrwxrwx 1 root root 3 2010-03-16 18:44 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2010-03-16 18:44 /dev/cdrw -> sr0
francisco@francisco-desktop:~$ ls -l /dev/cdr*
lrwxrwxrwx 1 root root 3 2010-03-16 18:44 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2010-03-16 18:44 /dev/cdrw -> sr0

```

---

### Post by J V on 2010-03-16
check the hardware, if the power cable is in the drive will try to read the disc but without the sata/ide connection it can't send any info...

---

### Post by franciskus on 2010-03-17
> **J V said:**
> check the hardware, if the power cable is in the drive will try to read the disc but without the sata/ide connection it can't send any info...It is connected (as shown in previous message):
```
Attached to: #14 (IDE interface)
```

---

### Post by hellblazer on 2010-06-09
I have a similar problem in Lucid.

I had a cd in and copied some stuff from it. Then I ejected it and inserted a data dvd that has worked before, but it won't mount.

...

And you wouldn't believe it but as I was writing this post I found the answer.

I had a terminal open that was still in a directory on the cd I ejected, so the new one didn't want to mount because the old one was still being used.

I changed the directory in the terminal and now my dvd is mounted

:D

Hope this helps

---

