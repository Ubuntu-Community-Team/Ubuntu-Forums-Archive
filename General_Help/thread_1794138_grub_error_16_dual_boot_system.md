---
title: "grub error 16 dual boot system"
date: 2011-06-30
forum: General Help
---

### Post by mesocyclone on 2011-06-30
My laptop, which has a long had a dual boot XP/Ubuntu installed, now gives the following error when booting:

[B]GRUB Loading stage 1.5.

GRUB Loading. plesae wait...[/B] [B]
Error 16[/B]

I booted a hot dvd to explore/fix, but am not sure where to go from here. 

sudo fdisk -l yields (manually typed in here, start/end not shown)

[B]Device     Boot   Id System:
/dev/sda1 *        7 HPFS/NTFS
/dev/sda2           f  W95 EXT'd (LBA)
/dev/sda3          82 Linux swap / Solaris
/dev sda5          7  HPFS/NTFS[/B]

I determined that /dev/sda1 appears to be the primary windows partition. sda2 won't mount without specifying a file type - I suspect it is the Linux partition. sda5 has one entry: System Volume Information.

I'd really like to preserve the Windows install - I don't have the Toshiba original install disks (sigh).

---

### Post by ajgreeny on 2011-06-30
Click on the Boot-info-script in my signature and follow the instructions there then post the RESULTS.txt file back here in code tags, the # icon in the toolbar of the reply box.

---

### Post by oldfred on 2011-06-30
Run the boot script as it may tell a little more as ajgreeny suggests.

But your fdisk did not show a Linux partition. Error 16 is from grub legacy. Are you missing a partition that has problems?
[http://members.iinet.net.au/~herman546/p15.html#16](http://members.iinet.net.au/~herman546/p15.html#16)

---

### Post by mesocyclone on 2011-06-30
Thanks. Ran the script. Results are below.

This is an old system and I don't remember if it still had a Linux partition on it.

My goal is to get the Windows to boot, but it had been set up as dual boot, with Grub.

In the output below, THEPENDRIVE is a pen drive I used for the script and its results.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21842183

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    77,610,014    77,609,952   7 NTFS / exFAT / HPFS
/dev/sda2          77,610,015   153,195,839    75,585,825   f W95 Extended (LBA)
/dev/sda5          77,610,078   153,195,839    75,585,762   7 NTFS / exFAT / HPFS
/dev/sda3         153,195,840   156,296,384     3,100,545  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1021 MB, 1021125120 bytes
255 heads, 63 sectors/track, 124 cylinders, total 1994385 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c11f82f

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     1,994,384     1,994,322   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2C6CA7446CA707A2                       ntfs       SQ004207P01
/dev/sda3        3cd0b82b-4ac3-4483-acc4-9660b53b297d   swap       
/dev/sda5        C2C8BF9EC8BF8F63                       ntfs       New Volume
/dev/sdb1        0C49-1636                              vfat       THEPENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/THEPENDRIVE       vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

```

---

### Post by oldfred on 2011-06-30
The grub legacy you have in the MBR is trying to boot from sda2 which now is the extended partition.

You can just restore the XP boot loader with fixMBR.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or if you cannot find XP cd, you can install lilo's boot loader which works just like windows in looking for a boot partition and jumping to that partition to boot.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by mesocyclone on 2011-07-01
Thanks! The lilo trick did the job and I now have my Windows back.

---

