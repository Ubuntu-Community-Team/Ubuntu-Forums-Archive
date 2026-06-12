---
title: "Grub Fails w/ Raid Setup"
date: 2011-09-03
forum: General Help
---

### Post by mi_di on 2011-09-03
Ok so I have a Intel i7 QM2820 with Windows seven and I tried to install Ubuntu 11.04 on it, I used Windows to create a 100G partition and then I followed [these instructions]("http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/") to set up my installation with the only difference that I only specified one partition for / and none for /home/.

After "successfully" installing I got the grub rescue prompt but I'm unable to make any progress from it:

```

grub rescue> ls
(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
grub rescue> ls (hd0,msdos3)
error: unknown filesystem.
grub rescue> ls (hd0,msdos2)
error: unknown filesystem.
grub rescue> ls (hd0,msdos1)
error: unknown filesystem.
grub rescue> set
prefix=(hd0,5)/grub
root=hs0,5
grub rescue> ls (hd0,5)
error: no such partition.
grub rescue> ls (hd0,4)
error: no such partition.
grub rescue> ls (hd0,3)
error: unknown filesystem.
grub rescue> ls (hd0,2)
error: unknown filesystem.
grub rescue> ls (hd0,1)
error: unknown filesystem.

```

I don't understand why ls doesn't give me the standard (hdX,Y), that everyone else seems to get, I also don't understand why partitions (hd0,1-3) seem to be recognized as existent (although under an unknow filesystem).

So I boot from the live CD and tried to find my Ubuntu partition but it doesn't seem to be recognized. Here is a snapshot from gParted:

[ATTACH]201425[/ATTACH]

And here is the output from boot_info_script.sh

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 94bab023-8157-45e4-8ac3-bd6d18557141 root 
    set 
    prefix=($root)/grub--------------------------------------------------------
    ------------------------.
 => Grub2 (v1.99) is installed in the MBR of 
    /dev/mapper/isw_ccgbgdcgdi_M17X_RAID0 and looks at sector 1 of the same 
    hard drive for core.img. core.img is at this location and uses an embedded 
    config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 94bab023-8157-45e4-8ac3-bd6d18557141 root 
    set 
    prefix=($root)/grub--------------------------------------------------------
    ------------------------.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ccgbgdcgdi_M17X_RAID01: ____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ccgbgdcgdi_M17X_RAID02: ____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ccgbgdcgdi_M17X_RAID03: ____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    20,496,383    20,414,464   7 NTFS / exFAT / HPFS
/dev/sda3          20,496,384 2,720,571,391 2,700,075,008   7 NTFS / exFAT / HPFS

/dev/sda3 ends after the last sector of /dev/sda

Drive: isw_ccgbgdcgdi_M17X_RAID0 _____________________________________________________________________

Disk /dev/mapper/isw_ccgbgdcgdi_M17X_RAID0: 1500.3 GB, 1500308045824 bytes
255 heads, 63 sectors/track, 182402 cylinders, total 2930289152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_ccgbgdcgdi_M17X_RAID01                 63        80,324        80,262  de Dell Utility
/dev/mapper/isw_ccgbgdcgdi_M17X_RAID02   *         81,920    20,496,383    20,414,464   7 NTFS / exFAT / HPFS
/dev/mapper/isw_ccgbgdcgdi_M17X_RAID03         20,496,384 2,720,571,391 2,700,075,008   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_ccgbgdcgdi_M17X_RAID0p1 5450-4444                              vfat       DellUtility
/dev/mapper/isw_ccgbgdcgdi_M17X_RAID0p2 0E00458C00457C29                       ntfs       RECOVERY
/dev/mapper/isw_ccgbgdcgdi_M17X_RAID0p3 B0D25D47D25D1348                       ntfs       OS
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_ccgbgdcgdi_M17X_RAID0
isw_ccgbgdcgdi_M17X_RAID0p1
isw_ccgbgdcgdi_M17X_RAID0p2
isw_ccgbgdcgdi_M17X_RAID0p3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on isw_ccgbgdcgdi_M17X_RAID01


Unknown BootLoader on isw_ccgbgdcgdi_M17X_RAID02


Unknown BootLoader on isw_ccgbgdcgdi_M17X_RAID03



========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/mapper/isw_ccgbgdcgdi_M17X_RAID01: No such file or directory
hexdump: /dev/mapper/isw_ccgbgdcgdi_M17X_RAID01: No such file or directory
hexdump: /dev/mapper/isw_ccgbgdcgdi_M17X_RAID02: No such file or directory
hexdump: /dev/mapper/isw_ccgbgdcgdi_M17X_RAID02: No such file or directory
hexdump: /dev/mapper/isw_ccgbgdcgdi_M17X_RAID03: No such file or directory
hexdump: /dev/mapper/isw_ccgbgdcgdi_M17X_RAID03: No such file or directory

```


So did I actually installed Ubuntu? can I get windows to boot again without having to do a system recovery?

Thanks so much in advance.

---

### Post by mi_di on 2011-09-04
Well I've gathered more information that might be useful, but I still have no idea of what to try next.

fdisk output:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x716150eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *           6        1276    10207232    7  HPFS/NTFS
/dev/sda3            1276      169348  1350037504    7  HPFS/NTFS

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0a0b0000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/dm-0: 1500.3 GB, 1500308045824 bytes
255 heads, 63 sectors/track, 182402 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x716150eb

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1           5       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/dm-0p2   *           6        1276    10207232    7  HPFS/NTFS
/dev/dm-0p3            1276      169348  1350037504    7  HPFS/NTFS

Disk /dev/dm-1: 41 MB, 41094144 bytes
255 heads, 63 sectors/track, 4 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 98816 bytes
Disk identifier: 0x8a42b4c3

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1            1880      111816   883058677+  cd  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 190, 62) logical=(1879, 146, 63)
Partition 1 has different physical/logical endings:
     phys=(257, 19, 50) logical=(111815, 75, 50)
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-1p2   ?       33873      138704   842053558   72  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(101, 107, 32) logical=(33872, 185, 42)
Partition 2 has different physical/logical endings:
     phys=(370, 114, 47) logical=(138703, 139, 40)
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-1p3   ?       69058       69060       10020+  45  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(68, 114, 0) logical=(69057, 206, 23)
Partition 3 has different physical/logical endings:
     phys=(322, 76, 12) logical=(69059, 14, 29)
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.

Disk /dev/dm-2: 10.5 GB, 10452205568 bytes
255 heads, 63 sectors/track, 1270 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-2p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-2p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/dm-2p4   ?      177065      177069       27487   43  Unknown
Partition 4 does not end on cylinder boundary.
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 1382.4 GB, 1382438404096 bytes
255 heads, 63 sectors/track, 168071 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-3p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-3p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-3p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/dm-3p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

```

This is what mount gives me

```

ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

Thanks.

---

### Post by mi_di on 2011-09-05
Well I was unable to find a workaround for the problem so I decided to install ubuntu 10.04 LTS which I have in my old laptop. The live CD still didn't recognize any ubuntu partition I told it to make exactly the same partitions that I specified when trying with 11.04.

The installation worked, and now I'm able to boot both to Windows and ubuntu 10.04. I didn;t even need the nomodeset option which was required to boot from the 11.04 live CD.

I still would like to have the latest ubuntu version, so suggestions are still welcome.

---

