---
title: "how to fix ubuntu boot (no such partition:rescue grub&gt;)"
date: 2010-07-08
forum: General Help
---

### Post by safyras on 2010-07-08
then my computer starts black window opens error : no such partition
                                                                         grub rescue>



I need help .I am new in linux



[HTML]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,801,920   326,360,474   295,558,555   7 HPFS/NTFS
/dev/sda4         512,161,790   625,139,711   112,977,922   f W95 Ext d (LBA)
/dev/sda5         552,075,264   625,139,711    73,064,448   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8027 MB, 8027897856 bytes
5 heads, 32 sectors/track, 97996 cylinders, total 15679488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064    15,679,487    15,671,424   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        FA6045A960456E07                       ntfs       RECOVERY                      
/dev/sda3        EE607586607555F5                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        1CCA7F0BCA7EE106                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdc1        E6A9-99C3                              vfat       KINGSTON                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/OS_               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  63 63 63 63 63 63 63 63  63 63 63 63 63 63 63 63  |cccccccccccccccc|
*
000001b0  63 63 63 63 63 63 63 63  63 63 63 63 63 63 00 fe  |cccccccccccccc..|
000001c0  ff ff 07 fe ff ff 02 08  61 02 00 e0 5a 04 00 00  |........a...Z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb [/HTML]P.S i tried [http://ubuntuforums.org/showthread.php?t=1326788](http://ubuntuforums.org/showthread.php?t=1326788) ,but this solution seems not working for me

---

### Post by safyras on 2010-07-08
i realy need fast help , becouse at this moment i am using live cd

---

### Post by safyras on 2010-07-08
good help...
one of solutions reinstall ubuntu via live cd/usb/dvd/ect...
if u have multi-boot reinstalling ubuntu will not delete anything it just rewrite old ubuntu i guess...

---

### Post by louieb on 2010-07-08
The  boot info script shows it looks for GRUB on sda6 but the fdisk output shows its not there. Wonder what happened to it. 

Other that Grub in the MBR of sda the boot info script shows not sign of a Linux installation. Did you delete the partition you installed Linux in?

---

