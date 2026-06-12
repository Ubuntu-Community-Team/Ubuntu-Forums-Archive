---
title: "Unable to locate my linux partition"
date: 2011-11-09
forum: General Help
---

### Post by pestilence000 on 2011-11-09
Okay, my first post on the forum and let me jump directly into my problem, any help would be highly appreciated. First, my PC got power failure accidently, because i was using my laptop without a battery. Then I restarted ubuntu, only to find disk checking....with errors and telling me to run manually. Bored by that, I shutdown and boot into windows. I use blah..blah.....but then I did something terribly wrong. I re-parttioned some of my NTFS drive, then blah...blah.....shutdown. Now, when i try to boot i get the _grub rescue>_ prompt. I use my ubuntu (11.10) live cd and re-install the windows bootloader (BECAUSE I CANNOT LOCATE MY LINUX PARTTION ANYWHERE). Now, i can easily boot into windows, and using easyBCD i install a linux loader....taking me to _grub_> prompt. I use all the commands out there but still i cannot locate my linux partition. I use the live cd but still no results. I then used LINUX DATA SAVER (or something ---to save any data from my linux partition), however, it reaches upto 4% and tehn it gives errors upon which my windows also starts responding slowly. 

  I don't know if i kinda sound dumb....since i already overwrite the mbr with the windows bootloader...here is the statistics from 'Boot Info Script' ([http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)) .....where the hell is my LINUX ext2 FileSystem ..??

> 

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 16388 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27169b4e

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   440,475,623   440,473,576   7 NTFS / exFAT / HPFS
/dev/sda2         440,475,648   597,766,143   157,290,496   7 NTFS / exFAT / HPFS
/dev/sda3         597,766,144   625,135,615    27,369,472   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2031 MB, 2031091712 bytes
255 heads, 63 sectors/track, 246 cylinders, total 3966976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              1     3,966,975     3,966,975   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FA4A35464A3500C5                       ntfs       
/dev/sda2        CE3CD0B13CD09635                       ntfs       New Volume
/dev/sda3        529629F69629DB6D                       ntfs       RECOVERY
/dev/sdb1        0434-243A                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/FA4A35464A3500C5  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /cdrom                   vfat       (rw)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)




---

### Post by pestilence000 on 2011-11-09
and btw, running fdisk -l on the terminal yields

> 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27169b4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27419   220236788    7  HPFS/NTFS
/dev/sda2           27419       37210    78645248    7  HPFS/NTFS
/dev/sda3           37210       38913    13684736    7  HPFS/NTFS

Disk /dev/sdb: 2031 MB, 2031091712 bytes
255 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         247     1983487+   b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 254, 63) logical=(0, 0, 2)
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(246, 237, 55)



---

