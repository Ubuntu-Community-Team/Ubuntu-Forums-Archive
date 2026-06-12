---
title: "stuck at grub rescue! have results.txt ready"
date: 2010-12-22
forum: General Help
---

### Post by cyfjeff on 2010-12-22
this is the results txt i get, please help

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 70. But according to the info from fdisk, 
                       sda5 starts at sector 111459040.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 70. But according to the info from fdisk, 
                       sda6 starts at sector 205278640.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 70. But according to the info from fdisk, 
                       sda7 starts at sector 306327490.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 70. But according to the info from fdisk, 
                       sda8 starts at sector 381286780.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    29,362,175    29,360,128   7 HPFS/NTFS
/dev/sda2    *     29,362,224   111,458,969    82,096,746   7 HPFS/NTFS
/dev/sda3         111,458,970   488,392,064   376,933,095   5 Extended
/dev/sda5         111,459,040   205,278,569    93,819,530   7 HPFS/NTFS
/dev/sda6         205,278,640   306,327,419   101,048,780   7 HPFS/NTFS
/dev/sda7         306,327,490   381,286,709    74,959,220   7 HPFS/NTFS
/dev/sda8         381,286,780   445,610,969    64,324,190   7 HPFS/NTFS
/dev/sda9         445,611,033   488,392,064    42,781,032   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       15bb4662-477e-4fbe-afac-85df49e8163e   ext4                                     
/dev/sda1        84E27239E2722F92                       ntfs       regular                       
/dev/sda2        9CA2BA41A2BA1FA6                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        2539F15FDD32F60C                       ntfs                                     
/dev/sda6        C8C588B2CA8F18A5                       ntfs       Music                         
/dev/sda7        4FB0DA08F75D733F                       ntfs       Web                           
/dev/sda8        41622303581D0A74                       ntfs                                     
/dev/sda9        157DE8F55403CE57                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
```

---

### Post by bcbc on 2010-12-22
Boot a windows repair disc and reinstall the windows bootloader:
```
bootrec.exe /fixmbr
```

You can also use lilo. See this thread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Problem #1, Solution #1 or #2.

---

### Post by cgroza on 2010-12-22
Try reinstalling GRUB.

---

### Post by oldfred on 2010-12-22
cgroza, wubi is a special case. It uses the windows boot loader, not grub to boot. 

OP
Follow bcbc's instructions to get a windows boot loader back into the MBR.

---

### Post by cgroza on 2010-12-22
I took a better look on the results.txt and I noticed this:

```
sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```
This might mean a corrupted file system and I do not know if installing Lilo would fix it.

---

### Post by cyfjeff on 2010-12-22
thanks guys

what happened is that i had windows 7 before and installed ubuntu using the wubi,  I was doing some updates and after the restart, i got the grub rescue screen.    Waiting to see more solutions, thanks

I was hoping i can get it fixed by using the ubuntu live CD, but looks like i have to use the windows vista DVD?

---

### Post by bcbc on 2010-12-22
If you follow that link I gave you, you can fix it from a live CD by installing lilo. It makes no difference whether you use lilo or the windows bootloader.

@cgroza, sometimes the bootinfoscript can't open the root.disk - it doesn't always mean there's a problem. If there is usually an fsck will fix it.

---

### Post by cyfjeff on 2010-12-22
thanks, will try and let you know the results

> **bcbc said:**
> If you follow that link I gave you, you can fix it from a live CD by installing lilo. It makes no difference whether you use lilo or the windows bootloader.

@cgroza, sometimes the bootinfoscript can't open the root.disk - it doesn't always mean there's a problem. If there is usually an fsck will fix it.

---

### Post by cyfjeff on 2010-12-22
it worked!!! thanks a lot, appreciate it

> **bcbc said:**
> If you follow that link I gave you, you can fix it from a live CD by installing lilo. It makes no difference whether you use lilo or the windows bootloader.

@cgroza, sometimes the bootinfoscript can't open the root.disk - it doesn't always mean there's a problem. If there is usually an fsck will fix it.

---

### Post by bcbc on 2010-12-23
> **cyfjeff said:**
> it worked!!! thanks a lot, appreciate it

Great! You're welcome :D

---

