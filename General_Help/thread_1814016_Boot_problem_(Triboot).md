---
title: "Boot problem (Triboot)"
date: 2011-07-28
forum: General Help
---

### Post by lithmariel on 2011-07-28
I was trying to install Mac, Windows and Linux on the same HD, but it didn't work well, so I ended having Mac and Linux on first HD and Windows on second.

After everything was installed, windows wouldn't boot. I "solved" this by editing grub.cfg (with "gksudo gedit /boot/grub/grub.cfg") so windows would be (hd1) instead of (hd1,1), which was the problem.

All OSes load now, but its all messed up.

MBR is grub, but it doesn't work, so I use iboot instead (mac loader in a CD). From there I can get to mac, if I want to go for linux, I choose linux there, and it takes me to grub, which can take me to linux and windows.
(I was trying to make chamaleon the MBR actually, as there are many guides and it seemed easy, so I don't know why grub is there, it shouldn't, I even deleted it and reinstalled to make sure it was on linux partition)

Here's some info from boot info script.
```
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    724989472 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => Windows is installed in the MBR of /dev/sdb.

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

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 724989312 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 3 for /boot/grub.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2             409,640   488,687,879   488,278,240  af HFS / HFS+
/dev/sda3    *    498,219,008   781,422,591   283,203,584  83 Linux
/dev/sda4         488,689,664   498,219,007     9,529,344  82 Linux swap / Solaris


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         409,640   488,687,879   488,278,240 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda3     498,219,008   781,422,591   283,203,584 Data partition (Windows/Linux)
/dev/sda4     488,689,664   498,219,007     9,529,344 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   625,121,279   625,121,217   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        70D6-1701                              vfat       EFI
/dev/sda2        d82d3f8d-edac-32c1-9abe-4ca5d6b4f51b   hfsplus    A snow leopard
/dev/sda3        a37e6312-ed88-409e-a9eb-51d70c49f727   ext4       
/dev/sda4        61410375-158a-436e-b12a-fcfb78d4b165   swap       
/dev/sdb1        1640F45440F43BD5                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sr0          /media/NEWISO            iso9660     (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda3/boot/grub/grub.cfg: ===========================

```I want to be able to load without needing a CD, basically, I want grub to work. But mac won't load from grub. And there's also the problem with grub not loading on MBR (would reinstalling fix it?)

---

