---
title: "(noob)After update manager reboot, ubuntu 10.10 doesn't work"
date: 2010-10-21
forum: General Help
---

### Post by masterblaster8987 on 2010-10-21
I have a duel boot (Vista/ Ubuntu) system . Last week I updated to 10.10. Yesterday I used the update manager and it downloaded/installed the updates. It required reboot. When the computer restart I was asked to choose the OS (normal) but this time Ubuntu wouldn't start. It just goes back to the OS selection screen. Disk check was normal. Here are the results from the boot info script.I am of course a noob to Ubuntu so a explanation and a easy fix will be greatly appreciated!!:) Thanks.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

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
Disk identifier: 0x131d2836

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   625,139,711   625,137,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       592cee5b-e897-463c-ac88-24b8188c61f8   ext4                                     
/dev/sda1        FAAE02C9AE027DFF                       ntfs                                     
/dev/sdb1        782E-CCF5                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/782E-CCF5         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by bcbc on 2010-10-21
The upgrade to 10.10 is known to corrupt the wubildr giving the symptoms you have. But usually this happens during the upgrade, not a week later.

However, you can try the upgrade 'fix' first as it sounds similar - and is easy to try.
Backup c:\wubildr 
Copy c:\ubuntu\winboot\wubildr over c:\wubildr

Try to get in to ubuntu.

If you have important data and you're concerned, now'd be a good time to backup the c:\ubuntu\disks\root.disk file. Or google and download a tool called ext2read - it can view files on the root.disk (read-only, but you can copy important data off).

---

### Post by masterblaster8987 on 2010-10-22
Thanks :)

---

