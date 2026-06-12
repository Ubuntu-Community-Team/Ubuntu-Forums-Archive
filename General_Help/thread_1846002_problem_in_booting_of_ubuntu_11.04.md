---
title: "problem in booting of ubuntu 11.04"
date: 2011-09-18
forum: General Help
---

### Post by sinaphysics on 2011-09-18
Hi
It's 3 months which i use ubuntu 11.04 and i'm so happy of it. but today when i choose ubuntu i face with some errors. i see that it can't find a device and something like below :
1. error ubuntu/disk/root.disk
2. error install/boot/grub/grub.cfg
i think it can't find these.
i see some posts in my last searches which they suggest about "sudo update-grub" , but when i type i see that sudo isn't supported. 
what do u suggest?
i add these that i have installed the ubuntu throughout vista.
when i type in grub>linux i see this which kernel not found.
please attend that i haven't cd-rom, i use just flash. if u suggest something it's better be in base of flash.

---

### Post by Rubi1200 on 2011-09-18
Hi and welcome to the forums :)

Please post the results of the boot info script so we can see what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by searchfgold6789 on 2011-09-18
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Please post the results of the boot info script so we can see what is going on.

There is a link at the bottom of my post with instructions.

Thanks.
I would recommend seeing the wubi megathread in his sig as well.

---

### Post by sinaphysics on 2011-09-18
the result.txt is
>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2    *        178,176    82,589,695    82,411,520   7 NTFS / exFAT / HPFS
/dev/sda3          82,589,696   312,578,047   229,988,352   f W95 Extended (LBA)
/dev/sda5          82,591,744   246,431,743   163,840,000   7 NTFS / exFAT / HPFS
/dev/sda6         246,433,792   312,578,047    66,144,256   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,897,087     7,897,025   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       6c5e8b37-1808-7342-b7aa-d5f76a0e75b7   ext2       casper-rw
/dev/sda1        07D8-071E                              vfat       DellUtility
/dev/sda2        04B087CBB087C222                       ntfs       
/dev/sda5        EA72E0A172E0742B                       ntfs       New Volume
/dev/sda6        A4B812A2B81272D2                       ntfs       New Volume
/dev/sdb1        D263-113B                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/04B087CBB087C222  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/New Volume_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script060/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected



---

### Post by Rubi1200 on 2011-09-18
Hi,
you appear to be missing the root.disk which is essential for Wubi to boot.

Check out this page from forum member bcbc:
[http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

---

### Post by sinaphysics on 2011-09-18
@rubi1200 you were right. this blog helped me to recreate disk and restore my missing files. how can u know of Result.txt that i lose Wubi ?
if i only install ubuntu on my system, do i have this problem ? or this is a problem  caused by windows vista ?   :KS

---

### Post by Rubi1200 on 2011-09-18
First, I am glad you managed to restore the root.disk and can boot Ubuntu again.

To answer your questions:
> how can u know of Result.txt that i lose Wubi ?
Take a look at sda5, where you installed it, and you can see the results:
> Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr
The files are missing. If you run the boot script now when everything is normal again, you will see what I mean.

> if i only install ubuntu on my system, do i have this problem ?
No. This is a problem with Wubi installs.

> or this is a problem  caused by windows vista ?
Not Windows Vista specifically, but all versions of Windows. There are various reasons why this might happen but you need to remember that Wubi is installed as one big file inside Windows. Any problems on the Windows side have the potential to affect a Wubi install including defragmentation, file corruption etc.

---

### Post by sinaphysics on 2011-09-19
i do it again and the result is
> sda5/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab


i see the changes. thank you a lot.

---

