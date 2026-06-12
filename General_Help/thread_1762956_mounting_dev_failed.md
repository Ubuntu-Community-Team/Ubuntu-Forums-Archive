---
title: "mounting /dev failed"
date: 2011-05-19
forum: General Help
---

### Post by Leelu3 on 2011-05-19
OK I know that this is a well covered topic... But I am still having problems fixing it and I have been all over these forums. Usually that does the trick... but not this time.

After a dirty shut down (lost power mid program install)  I get the same story as everyone else:
mounting /dev on /root/dev failed: No such file or directory  etc...

this is what I get when I run the boot_info_script.sh

```
                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    137394072 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 4 for /boot/burg.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

hda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/syslinux/syslinux.cfg

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2    *        409,640    78,298,239    77,888,600  af HFS / HFS+
/dev/sda3          78,301,184   153,008,127    74,706,944  83 Linux
/dev/sda4         153,008,128   156,301,311     3,293,184  82 Linux swap / Solaris


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         409,640    78,298,239    77,888,600 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda4      78,301,184   153,008,127    74,706,944 Data partition (Windows/Linux)
/dev/sda5     153,008,128   156,301,311     3,293,184 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4105 MB, 4105175040 bytes
37 heads, 37 sectors/track, 5856 cylinders, total 8017920 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,760     8,017,919     8,015,160   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/hda                                                iso9660    SLAX
/dev/sda2        6D1B3D02877C9E2B                       hfsplus    Grrr...
/dev/sda3        10c8f93e-14e5-4ce1-81cb-ce8239dcb532   ext4       
/dev/sda4        d293e7c9-e5cb-43c4-85e2-b873b0dedcf0   swap       
/dev/sdb1        3433-3231                              vfat       UDISK

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/hda         /mnt/hda                 iso9660    (ro,noatime)
/dev/sdb1        /mnt/sdb1                vfat       (rw,noatime,quiet,umask=0,check=s,shortname=mixed)


======================= hda/boot/syslinux/syslinux.cfg: ========================

--------------------------------------------------------------------------------
INCLUDE /boot/slax.cfg
--------------------------------------------------------------------------------

==================== hda: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/initrd.gz
            ?? = ??             boot/vmlinuz

================== hda: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/syslinux/syslinux.cfg

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: Bad file descriptor
mdadm: No arrays found in config file


```
 

The OSX half of the partition works fine.  I can not load an Ubuntu LiveCD or LiveUSB.  To get this info I had to use the Slax distro...


From here I am lost... any suggestions?

---

### Post by Leelu3 on 2011-05-19
... Oook then,  Am I posting this in the wrong spot?  I thought it would be better to start a new thread rather than tack this on someone else's problem.

---

