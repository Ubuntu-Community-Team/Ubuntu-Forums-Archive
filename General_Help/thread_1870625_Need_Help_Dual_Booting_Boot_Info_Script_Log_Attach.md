---
title: "Need Help Dual Booting *Boot Info Script* Log Attached"
date: 2011-10-27
forum: General Help
---

### Post by FenderHSS on 2011-10-27
This problem has been plaguing me for over a month. First on Natty and now on Oneric. I can't boot into Windows 7 using Grub (2?). All I get is a blinking (indefinitely) cursor. Since my hard drive is GPT, I have used GPTsync, but to no success. I also can not use the system recovery from my Windows 7 disc (I also tried the SP1 disc). Here are my boot info script results:
>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    402038939 of the same hard drive for core.img. core.img is at this 
    location and looks for  on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 403638539 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda4 
                       and looks at sector 403522747 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1            39            39  ee GPT
/dev/sda2    *             40       409,639       409,600   c W95 FAT32 (LBA)
/dev/sda3             409,640   391,034,639   390,625,000  af HFS / HFS+
/dev/sda4         508,485,632 1,250,263,039   741,777,408   7 NTFS / exFAT / HPFS


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 Data partition (Windows/Linux)
/dev/sda2         409,640   391,034,639   390,625,000 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda3     508,485,632 1,250,263,039   741,777,408 Data partition (Windows/Linux)
/dev/sda4     391,298,131   508,485,631   117,187,501 EFI System partition

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        70D6-1701                              vfat       EFI
/dev/sda2        45023f56-e909-3842-b8f3-400663f6191b   hfsplus    MAC
/dev/sda3        88F2EB10CD0EB400                       ntfs       
/dev/sda4        c105a752-9355-451f-8f6d-4c3996b104ce   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/MAC               hfsplus    (ro,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/88F2EB10CD0EB400  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /                        ext3       (rw,errors=remount-ro,user_xattr)


=========================== sda4/boot/grub/grub.cfg: ===========================/dev/sda1 and /dev/sda2 are operating systems that I don't really care about. All I want is to dual boot /dev/sda3 (Windows 7) and /dev/sda4 (Ubuntu). All suggestions are welcome

---

### Post by oldfred on 2011-10-27
I use gpt but not the hybrid MBR you have to have with Windows. But you have installed grub2's boot loader to the Windows PBR or partition boot sector. 

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

Using any tools on a hybrid like this is dangerous as it is part MBR and part gpt and if they get out of sync then you have major issues.

But I think you can use testdisk to see if it will restore the PBR. Not sure if testdisk will see it as gpt or MBR??

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by FenderHSS on 2011-10-27
That testdisc is quite a useful tool. I used it to repair the Windows Partition after using the fixmbr tool.

Unfortunately, after following instructions in that reforge link, there are no results (just a blinking cursor). Do you know how to enable error reporting in Grub? I remember on Natty whenever I booted into Windows Grub would give me an error. I am pretty sure the error stayed the same, it just got replaced by a blinking cursor.

Thanks for the help

---

### Post by oldfred on 2011-10-27
I really do not understand how Mac's boot with the mixed MBR/gpt. Windows normally boots via the MBR and grub then overwrites the MBR and chainloads to the PBR to boot windows. With Mac in there I do not know how you get to grub.

The fixMBR puts a Windows boot loader in the MBR, but that is not how a Mac boots.

---

