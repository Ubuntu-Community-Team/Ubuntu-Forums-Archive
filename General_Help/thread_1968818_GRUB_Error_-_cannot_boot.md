---
title: "GRUB Error - cannot boot"
date: 2012-04-29
forum: General Help
---

### Post by zanman on 2012-04-29
Greetings

I have done what I believe to be extensive Googling on this issue as well as looked through these forums, so I do not believe there is already a solution to this, but if I am mistaken then please direct me to it.

I have two harddrives, a 1TB main drive and a 60GB SSD.  I run Ubuntu 12.04 and Windows 7 both 64bit on the 1TB drive, and there are no operating systems on the SSD so I do not believe it will have much relevance in this matter. 

So a few weeks ago I upgraded to Ubuntu 12.04 LTS 64bit from 11.10 - everything went fine.  My system was running nicely since then, and then the other day I ran an 'apt-get update' followed by 'apt-get upgrade' to get everyhting up to date; while I am not certain something involving this is the culprit, I believe it may be because it booted fine the next time but after that I was stuck with the following at boot:

> error: ELF sections outside core.When I tried to run 'insmod /boot/grub/linux.mod' I was returned the same error.  So I went around the internet and followed this guide [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) but to no avail. Then after following this guide [http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html) I got a different error at boot:

> error: invalid arch independent ELF magic.While I do know that the latter of the errors has been experienced by many users, I have tried every solution I can find in an attempt to resolve it, including [http://ubuntuforums.org/showthread.php?t=1965810](http://ubuntuforums.org/showthread.php?t=1965810) but have had no luck.  I tried running boot-repair as well, including purging and reinstalling the latest kernel, but it did not work either.

Here is the output of bootinfoscript:

> Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of 
    /dev/mapper/isw_cacjbebhjj_DWW-ACRT3028092 and looks at sector 1 of the 
    same hard drive for core.img. core.img is at this location and looks for 
    (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

isw_cacjbebhjj_DWW-ACRT30280921: _______________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

isw_cacjbebhjj_DWW-ACRT30280923: _______________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cacjbebhjj_DWW-ACRT30280924: _______________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,280,063   488,278,016  83 Linux
/dev/sda3         488,280,064 1,819,480,063 1,331,200,000   7 NTFS / exFAT / HPFS
/dev/sda4       1,941,772,288 1,953,523,711    11,751,424   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    78,219,263    78,217,216   7 NTFS / exFAT / HPFS


Drive: isw_cacjbebhjj_DWW-ACRT3028092 _____________________________________________________________________

Disk /dev/mapper/isw_cacjbebhjj_DWW-ACRT3028092: 1000.2 GB, 1000204271616 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_cacjbebhjj_DWW-ACRT30280921   *          2,048   488,280,063   488,278,016  83 Linux
/dev/mapper/isw_cacjbebhjj_DWW-ACRT30280923        488,280,064 1,819,480,063 1,331,200,000   7 NTFS / exFAT / HPFS
/dev/mapper/isw_cacjbebhjj_DWW-ACRT30280924      1,941,772,288 1,953,523,711    11,751,424   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        af30efaf-e3af-4092-91b3-0c82d05e8267   ext4       
/dev/sda3        E0BA5497BA546BD2                       ntfs       
/dev/sda4        148FAF82341E1EEB                       ntfs       temp
/dev/sdb1        88FE7364FE734A08                       ntfs       ssd
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_cacjbebhjj_DWW-ACRT30280921


Unknown BootLoader on isw_cacjbebhjj_DWW-ACRT30280923


Unknown BootLoader on isw_cacjbebhjj_DWW-ACRT30280924



=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
hexdump: /dev/mapper/isw_cacjbebhjj_DWW-ACRT30280921: No such file or directory
hexdump: /dev/mapper/isw_cacjbebhjj_DWW-ACRT30280921: No such file or directory
hexdump: /dev/mapper/isw_cacjbebhjj_DWW-ACRT30280923: No such file or directory
hexdump: /dev/mapper/isw_cacjbebhjj_DWW-ACRT30280923: No such file or directory
hexdump: /dev/mapper/isw_cacjbebhjj_DWW-ACRT30280924: No such file or directory
hexdump: /dev/mapper/isw_cacjbebhjj_DWW-ACRT30280924: No such file or directoryAs well as the output of running 'ls' from the 'grub rescue>' line I get at boot:

> (hd0) (hd0,msdos4) (hd0,msdos3) (hd0,msdos1) (hd1) (hd1,msdos1)And this is what running 'ls /boot' from the grub rescue>' line I get at boot gives me:

> System.map-3.0.0-12-generic abi-3.0.0-12-generic config-3.0.0-12-generic memtest86+.bin memtest86+_multiboot.bin vmcoreinfor-3.0.0-12-generic vmlinuz-3.0.0-12-generic abi-3.0.0-13-generic initrd.img-3.0.0-12-generic config-3.0.0-13-generic System.map-3.0.0-13-generic vmcoreinfo-3.0.0-13-generic System.map-3.1.2-030103-generic vmlinuz-3.0.0.-13-generic initrd.img-3.0.0-13-generic abi-3.1.2-030103-generic config-3.1.2-030103-generic vmlinuz-3.1.2-030103-generic initrd.img-3.1.2-030103-genericNote I was previously running my system with kernel version 3.3.1 without issue up until this issue the other day.

Here is what 'sudo fdisk -l' gives from an Ubuntu 12.04 LTS 64bit LiveCD:

>  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488280063   244139008   83  Linux
/dev/sda3       488280064  1819480063   665600000    7  HPFS/NTFS/exFAT
/dev/sda4      1941772288  1953523711     5875712    7  HPFS/NTFS/exFAT

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    78219263    39108608    7  HPFS/NTFS/exFAT
Honestly at this point I would be willing to reinstall a Linux distro over my current Linux partition if my Windows partition could still be readily accessed from the new install, so if this seems like it cannot be fixed any advice on this would be appreciated as well.

Thank you in advance for your help.

---

### Post by zanman on 2012-04-29
bump?

---

