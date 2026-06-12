---
title: "Grub rescue problem"
date: 2010-05-21
forum: General Help
---

### Post by Hobbitsonic on 2010-05-21
Ok, so here's the story, I have an acer 322 gig computer and I recently installed ubuntu on it for dual booting purposes. Here's the problem. When I switch my computer on It comes ups with...

AMD Data Change...Update New Data To DMI!error: no such device: 46d787e1-c8aa-4c00-bbf1-659cfb5aecb4.
Grub Rescue>_

any help would be much appreciated
p.s if it helps, I booted and installed it from my mates memory stick

thanks =)

---

### Post by linuxman94 on 2010-05-21
See [this]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot") link to boot into ubuntu, then open up a terminal and type the following.

```
sudo update-grub
```

---

### Post by Hobbitsonic on 2010-05-22
So how do I do that, do I just put in a memory stick and switch it on?

---

### Post by wilee-nilee on 2010-05-22
I think your going to need to post this script to get any real definitive help.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Post in code tags using this method.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Hobbitsonic on 2010-05-22
I'd like to add that as soon as I switch my computer on, it goes straight to a black screen with the messge shown above

---

### Post by wilee-nilee on 2010-05-22
> **Hobbitsonic said:**
> I'd like to add that as soon as I switch my computer on, it goes straight to a black screen with the messge shown above

You would run the script from the live cd or thumb.

---

### Post by Hobbitsonic on 2010-05-22
Ok I will try that and get back to you asap

---

### Post by Hobbitsonic on 2010-05-22
```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    38,799,359    38,797,312  27 Hidden HPFS/NTFS
/dev/sda2    *     38,799,360   625,139,711   586,340,352   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8054 MB, 8054636032 bytes
255 heads, 63 sectors/track, 979 cylinders, total 15731711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,731,666    15,731,604   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                 255     3,932,159     3,931,905   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5E766C29766C03DD                       ntfs       PQSERVICE                     
/dev/sda2        64321EDD321EB450                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F3DA-10F6                              vfat       CRUZER                        
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        164A-3730                              vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by volter on 2010-05-22
As I understand you laptop can find the grub.... so try to install it by using [**parted magic**]("http://partedmagic.com/"), I managed to restore my windows boot loader.

---

### Post by Hobbitsonic on 2010-05-22
I have downloaded the parted magic. How would i go about doing what you said?

---

### Post by volter on 2010-05-22
When you insert the CD & restart, choose Extras menu-> Super Grub 2/1 :twisted:(go with the instructions there).

Good luck :smile:.

---

### Post by Hobbitsonic on 2010-05-22
hi, ive found the menu, i have two options, boot ubuntu gnu/lnux  and AUTO MAGIC BOOT, the first one reboots the PC and brings up a windows failure message and the second days the thingy is aborted. Is this an issue with windows? :confused: thanks :)

---

### Post by volter on 2010-05-22
Sorry, but I didn't really try to install the Linux grub. Last time I was installing something it was Windows boot loader. 

Sorry  :-? !!!

---

