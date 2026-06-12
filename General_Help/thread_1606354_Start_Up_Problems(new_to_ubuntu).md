---
title: "Start Up Problems(new to ubuntu)"
date: 2010-10-26
forum: General Help
---

### Post by Deorwin on 2010-10-26
Hi, a few weeks ago I updated my ubuntu to 10.10 and it worked fine; I went a week or so w/o using that computer and I decided to get it out and start it up. After starting it up I decided I should update it, so i did. After updating I restarted my computer and this error came up when i tried to boot ubuntu"GNU GRUB version 1.98+20100804-5ubuntu3 Minimal BASH-like editing supposrted" (this is the first part of it). I am running a HP pavilion dv2000 and I used wubi to install ubuntu in windows seven, windows seven works fine; i ran a boot info script(assuming this is what its called) and i got this as a result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,394,751   488,187,904   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       f8fcb53f-cbb0-432c-972a-248bf225a62e   ext4                                     
/dev/sda1        EE4C1F054C1EC7EB                       ntfs       System Reserved               
/dev/sda2        CA2C21432C212BBF                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
```

Any help would be greatly appreciated ^_^

---

### Post by bcbc on 2010-10-26
Try this: [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

Yours is a little different since the upgrade worked fine for a while, but I'd try this first.

---

