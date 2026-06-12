---
title: "GRUB on RAID1 Ubuntu -  Windows7 on seperate disk, no boot after update"
date: 2012-07-11
forum: General Help
---

### Post by gdell on 2012-07-11
Hi there!

Here is my case:

There are 4 WD1002FAEX disks all on same controller (Intel RST)
Windows7Pro x64 on 1st, just some data on 2nd
3rd and 4th are mirrored (VOLUME_0) with Ubuntu 11.10 x64 on.

System booted nice until Ubuntu updated
Then all I have on the "GNU GRUB version 1.99-21ubuntu3" menu are
3 options for Linux (normal,recovery mode and previous versions),
2 options for memory testing and an option for Windows7.
All result to the same:
"error: no such partition.
error: no such partition.
error: no such partition.

Press any key to continue..."

when pressing e for edit on first line for Linux:
```
setparams 'Ubuntu, with Linux 3.2.0-24-generic'

recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd5,msdos1)'
search --no-floppy --fs-uuid --set=root 0c4ae55c-d001-4a67-96e8-2015d80\
c6808
linux /boot/vmlinuz-3.2.0-24-generic root=UUID=0c4ae55-d001-4a67-96e8-\
2015d80c6808 ro   quiet slash $vt_handoff
initrd /boot/initrd.img-3.2.0-24-generic
```and on the last line for Windows:
```
setparams 'Windows 7 (loader) (on /dev/sda1)'

insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 64A88F93A88F6282
chainloader +1
```boot-repair reported

```
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

md/imsm0: ______________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        64A88F93A88F6282                       ntfs       System Reserved
/dev/sda2        0026915A26915190                       ntfs       
/dev/sdb1        7A609C32765AE539                       ntfs       Data
/dev/sdc                                                isw_raid_member 
/dev/sdd                                                isw_raid_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr1         /live/image              iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on md/imsm0



=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[8243]) leaked on lvscan invocation. Parent PID 9916: bash
File descriptor 8 (pipe:[8243]) leaked on lvscan invocation. Parent PID 9916: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-07-09__10h57 ===================
boot-repair version : 3.18-0ppa39~lucid
boot-sav version : 3.191-0ppa2~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version : 3.18-0ppa14~lucid
boot-repair updated

BLKID BEFORE RAID ACTIVATION:
/dev/sda1: LABEL="System Reserved" UUID="64A88F93A88F6282" TYPE="ntfs"
/dev/sda2: UUID="0026915A26915190" TYPE="ntfs"
/dev/sdb1: LABEL="Data" UUID="7A609C32765AE539" TYPE="ntfs"
/dev/sdc: TYPE="isw_raid_member"
/dev/loop0: TYPE="squashfs"
/dev/sdd: TYPE="isw_raid_member"
dmraid -si -c: isw_cdjacjeebj_VOLUME_0
dmraid -ay:
RAID set "isw_cdjacjeebj_VOLUME_0" was not activated
dmraid -sa -c:
[dmraid] packages may interfer with MDraid. Do you want to remove them? yes
apt-get remove -y --force-yes dmraid
The following package was automatically installed and is no longer required:
libdmraid1.0.0.rc16
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
dmraid
0 upgraded, 0 newly installed, 1 to remove and 48 not upgraded.
(Reading database ... 43315 files and directories currently installed.)
Removing dmraid ...
I: update-initramfs is disabled (live system is running on read-only media).
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a 

controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Scanning MDraid Partitions
mdadm: No arrays found in config file or automatically
mdadm --detail --scan: ARRAY /dev/md/imsm0 metadata=imsm UUID=c63ed2c0:572532e8:3e04e478:2d473688
[dmraid] packages may interfer with MDraid. Do you want to remove them? yes
apt-get remove -y --force-yes dmraid
Package dmraid is not installed, so not removed
The following package was automatically installed and is no longer required:
libdmraid1.0.0.rc16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 48 not upgraded.
File descriptor 7 (pipe:[8243]) leaked on lvs invocation. Parent PID 5140: /bin/sh
File descriptor 8 (pipe:[8243]) leaked on lvs invocation. Parent PID 5140: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 02.07.2012 , squeeze , Debian , x86_64)
CPU op-mode(s):        32-bit, 64-bit
sdc (sda) has unknown type. Please report this message to yannubuntu@gmail.com
sdd (sda) has unknown type. Please report this message to yannubuntu@gmail.com

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain

=================== blkid:
/dev/sda1: LABEL="System Reserved" UUID="64A88F93A88F6282" TYPE="ntfs"
/dev/sda2: UUID="0026915A26915190" TYPE="ntfs"
/dev/sdb1: LABEL="Data" UUID="7A609C32765AE539" TYPE="ntfs"
/dev/sdc: TYPE="isw_raid_member"
/dev/loop0: TYPE="squashfs"
/dev/sdd: TYPE="isw_raid_member"


1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    

no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    

no-winload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    

nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    

no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    

haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    

nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    /mnt/boot-sav/sda2.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    

no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    

no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    

nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    /mnt/boot-sav/sdb1.

sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    

2048 sectors * 512 bytes
sdb    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    

63 sectors * 512 bytes

=================== parted -l:

Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  106MB   105MB   primary  ntfs
2      106MB   1000GB  1000GB  primary  ntfs         boot


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  1000GB  1000GB  primary  ntfs


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  997GB   997GB   primary   ext4            boot
2      997GB   1000GB  3499MB  extended
5      997GB   1000GB  3499MB  logical   linux-swap(v1)


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  997GB   997GB   primary   ext4            boot
2      997GB   1000GB  3499MB  extended
5      997GB   1000GB  3499MB  logical   linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.

                                                                          
Error: /dev/sr1: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr1 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,allow_other,blksize=4096)


/sys/block/md127:  alignment_offset bdi capability dev ext_range holders inflight md power queue 

range removable ro size slaves stat subsystem trace uevent
/sys/block/sda:  alignment_offset bdi capability dev device ext_range holders inflight power 

queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device ext_range holders inflight power 

queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device ext_range holders inflight power 

queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device ext_range holders inflight power 

queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device ext_range holders inflight power 

queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1:  alignment_offset bdi capability dev device ext_range holders inflight power 

queue range removable ro size slaves stat subsystem trace uevent
/dev:  block bsg btrfs-control bus cdrom cdrom1 cdrw cdrw1 char console core cpu_dma_latency disk 

dvd dvd1 dvdrw dvdrw1 fd full fuse hidraw0 hpet initctl input kmsg log MAKEDEV mcelog md md127 

mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 scd1 

sda sda1 sda2 sdb sdb1 sdc sdd sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sndstat sr0 sr1 stderr 

stdin stdout urandom v4l vbi0 vga_arbiter video0 xconsole zero
/mnt/boot-sav/sda2:  Boot bootmgr boot-sav Config.Msi csb.log Documents and Settings hiberfil.sys 

Install.log Intel NVIDIA pagefile.sys PerfLogs ProgramData Program Files Program Files (x86) 

Recovery $Recycle.Bin RHDSetup.log System Volume Information Users Windows

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    4.0G   57M  3.9G   2% /
tmpfs        tmpfs    4.0G     0  4.0G   0% /lib/init/rw
udev         tmpfs    3.9G  200K  3.9G   1% /dev
tmpfs        tmpfs    4.0G     0  4.0G   0% /dev/shm
/dev/sr1   iso9660    346M  346M     0 100% /live/image
tmpfs        tmpfs    4.0G   57M  3.9G   2% /live/cow
tmpfs        tmpfs    4.0G     0  4.0G   0% /live
tmpfs        tmpfs    4.0G  8.0K  4.0G   1% /tmp
/dev/sda1  fuseblk    100M   25M   76M  25% /mnt/boot-sav/sda1
/dev/sda2  fuseblk    932G   43G  890G   5% /mnt/boot-sav/sda2
/dev/sdb1  fuseblk    932G  115M  932G   1% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ce541fa

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005c85b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073fb4

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121176   973340672   83  Linux
/dev/sdc2          121176      121601     3417089    5  Extended
/dev/sdc5          121176      121601     3417088   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073fb4

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      121176   973340672   83  Linux
/dev/sdd2          121176      121601     3417089    5  Extended
/dev/sdd5          121176      121601     3417088   82  Linux swap / Solaris



=================== Recommended repair
recommendedrepair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda2.
Additional repair will be performed: unhide-bootmenu


Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 2 boot on

                                                                          
Information: You may need to update /etc/fstab.


Boot successfully repaired.

You can now reboot your computer.

paste.debian ko, using paste.ubuntu
```no luck.

fdisk -l from a 12.04 x64 Live CD reported:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ce541fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      206848  1953521663   976657408    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005c85b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073fb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  1946683391   973340672   83  Linux
/dev/sdc2      1946685438  1953519615     3417089    5  Extended
/dev/sdc5      1946685440  1953519615     3417088   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073fb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  1946683391   973340672   83  Linux
/dev/sdd2      1946685438  1953519615     3417089    5  Extended
/dev/sdd5      1946685440  1953519615     3417088   82  Linux swap / Solaris

Disk /dev/sde: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0012b451

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63    15663103     7831520+   b  W95 FAT32

Disk /dev/mapper/isw_cdjacjeebj_VOLUME_0: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073fb4

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cdjacjeebj_VOLUME_0p1   *        2048  1946683391   973340672   83  Linux
/dev/mapper/isw_cdjacjeebj_VOLUME_0p2      1946685438  1953519615     3417089    5  Extended
/dev/mapper/isw_cdjacjeebj_VOLUME_0p5      1946685440  1953519615     3417088   82  Linux swap / 

Solaris

Disk /dev/mapper/isw_cdjacjeebj_VOLUME_0p1: 996.7 GB, 996700848128 bytes
255 heads, 63 sectors/track, 121175 cylinders, total 1946681344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                                 Device Boot      Start         End      Blocks   Id  System

Disk /dev/mapper/isw_cdjacjeebj_VOLUME_0p2: 3499 MB, 3499099136 bytes
255 heads, 63 sectors/track, 425 cylinders, total 6834178 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                                 Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cdjacjeebj_VOLUME_0p2p1               2     6834177     3417088   82  Linux swap 

/ Solaris

Disk /dev/mapper/isw_cdjacjeebj_VOLUME_0p5: 3499 MB, 3499098112 bytes
255 heads, 63 sectors/track, 425 cylinders, total 6834176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cdjacjeebj_VOLUME_0p5 doesn't contain a valid partition table
ubuntu@ubuntu:~$ 

```Yann from boot-repair team said
> The problem is that your RAID remains inactive. I don't know how to help you if you can't 

activate it, sorry.
Please ask "How to activate my RAID?" on ubuntuforums.org and/or askubuntu.com .


When you find a solution, please tell me, and activate your RAID before running Boot-Repair. 

...so here I am.

Any ideas??

---

### Post by YannBuntu on 2012-07-12
Hi
Additional informations:
- the complete BootInfo report is: [http://paste.ubuntu.com/1082380](http://paste.ubuntu.com/1082380)
- the interesting part is:

```
dmraid -si -c: isw_cdjacjeebj_VOLUME_0
dmraid -ay:
RAID set "isw_cdjacjeebj_VOLUME_0" was **not activated**
dmraid -sa -c:
User chose to keep dmraid. It may interfer with mdadm.
Scanning MDraid Partitions
mdadm: No arrays found in config file or automatically
mdadm --detail --scan: ARRAY /dev/md/imsm0 metadata=imsm UUID=c63ed2c0:572532e8:3e04e478:2d473688
```

Does someone know how to activate this RAID?

---

### Post by mike acker on 2012-07-12
zounds&gadzooks!! sounds like Ubuntu supports RAID1

with 1TB and 2TB drives being de rigeure these days RAID1 makes a lot of sense

I totally new and green here so if I do something wrong just guide me in the right direction
thanks

yikes!!  I got another bean :-)

---

### Post by YannBuntu on 2012-07-12
**@mike acker:** please create your own new thread explaining your problem.

---

### Post by gdell on 2012-07-12
Hi all!
here's another piece of info
bootinfoscript ran from 12.04 live cd:
 ```
                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sde.
 => No boot loader is installed in the MBR of 
    /dev/mapper/isw_cdjacjeebj_VOLUME_0.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:  Syslinux looks at sector 12095416 of /dev/sde1 for 
                       its second stage. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

isw_cdjacjeebj_VOLUME_01: ______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

isw_cdjacjeebj_VOLUME_02: ______________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

isw_cdjacjeebj_VOLUME_05: ______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        206,848 1,953,521,663 1,953,314,816   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63    15,663,103    15,663,041   b W95 FAT32


Drive: isw_cdjacjeebj_VOLUME_0 _____________________________________________________________________

Disk /dev/mapper/isw_cdjacjeebj_VOLUME_0: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_cdjacjeebj_VOLUME_01   *          2,048 1,946,683,391 1,946,681,344  83 Linux
/dev/mapper/isw_cdjacjeebj_VOLUME_02      1,946,685,438 1,953,519,615     6,834,178   5 Extended
/dev/mapper/isw_cdjacjeebj_VOLUME_05      1,946,685,440 1,953,519,615     6,834,176  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_cdjacjeebj_VOLUME_0p1 0c4ae55c-d001-4a67-96e8-2015b80c6808   ext4       
/dev/mapper/isw_cdjacjeebj_VOLUME_0p5 45c666b4-2b6e-44c1-af6b-d3939f6b4a85   swap       
/dev/sda1        64A88F93A88F6282                       ntfs       System Reserved
/dev/sda2        0026915A26915190                       ntfs       
/dev/sdb1        7A609C32765AE539                       ntfs       Data
/dev/sdc                                                isw_raid_member 
/dev/sdd                                                isw_raid_member 
/dev/sde1        1045-B798                              vfat       
/dev/sr1                                                iso9660    Ubuntu 12.04 LTS amd64

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_cdjacjeebj_VOLUME_0
isw_cdjacjeebj_VOLUME_0p1
isw_cdjacjeebj_VOLUME_0p2
isw_cdjacjeebj_VOLUME_0p5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/1045-B798         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


============================== sde1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT memtest

LABEL memtest
    kernel mt86plus

PROMPT 0
TIMEOUT 0--------------------------------------------------------------------------------

================= sde1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_cdjacjeebj_VOLUME_01


Unknown BootLoader on isw_cdjacjeebj_VOLUME_02


Unknown BootLoader on isw_cdjacjeebj_VOLUME_05



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/isw_cdjacjeebj_VOLUME_01: No such file or directory
hexdump: /dev/mapper/isw_cdjacjeebj_VOLUME_01: No such file or directory
hexdump: /dev/mapper/isw_cdjacjeebj_VOLUME_02: No such file or directory
hexdump: /dev/mapper/isw_cdjacjeebj_VOLUME_02: No such file or directory
hexdump: /dev/mapper/isw_cdjacjeebj_VOLUME_05: No such file or directory
hexdump: /dev/mapper/isw_cdjacjeebj_VOLUME_05: No such file or directory


```

and grub.cfg mounted on /media/0c4ae55c-d001-4a67-96e8-2015b80c6808/boot/grub
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd5,msdos1)'
search --no-floppy --fs-uuid --set=root 0c4ae55c-d001-4a67-96e8-2015b80c6808
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd5,msdos1)'
  search --no-floppy --fs-uuid --set=root 0c4ae55c-d001-4a67-96e8-2015b80c6808
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 0c4ae55c-d001-4a67-96e8-2015b80c6808
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=0c4ae55c-d001-4a67-96e8-2015b80c6808 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 0c4ae55c-d001-4a67-96e8-2015b80c6808
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=0c4ae55c-d001-4a67-96e8-2015b80c6808 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 0c4ae55c-d001-4a67-96e8-2015b80c6808
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=0c4ae55c-d001-4a67-96e8-2015b80c6808 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 0c4ae55c-d001-4a67-96e8-2015b80c6808
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=0c4ae55c-d001-4a67-96e8-2015b80c6808 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 0c4ae55c-d001-4a67-96e8-2015b80c6808
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 0c4ae55c-d001-4a67-96e8-2015b80c6808
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 64A88F93A88F6282
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

Why does it NOT boot???
please help!
thanks

---

### Post by oldfred on 2012-07-13
I do not know RAID but liveCD does not have the RAID drivers, so boot script will not show the data inside the RAID. Yann's boot repair automatically downloads the extra drivers so it may see more info or if running script manually you need to add the extra drivers.

Often script works better for servers if these are added.

Is able to search LVM partitions if the LVM2 package is install, Fedora needs to be mounted to see it with os-prober
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install gawk
sudo apt-get install xz-utils
# unlzma is equivalent to xz --format=lzma --decompress.

You need to have grub2's boot loader installed to the root of the RAID if that is what you are booting from or /dev/mapper/isw_cdjacjeebj_VOLUME_0. You have syslinux boot loader which is a Windows type boot loader that will boot Windows or others with code in the partition boot sector of the partition with the boot flag.

---

### Post by gdell on 2012-09-11
Back from holidays.

The system finally worked!

This is what i did:

Boot from Live CD 11.10 x64

 open terminal
sudo fdisk -l
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
nautilus /mnt
(mnt opened containing all bin, boot, etc, home, root, ... folders)
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0
Installation finished.No error reported.
sudo umount /mnt
 exit terminal
reboot
Windows7 booted with no GRUB menu
reboot 
enter bios to change boot order to VOLUME_0 first 
reboot
GRUB menu. All options working.

Thanks everybody for their help.

---

### Post by YannBuntu on 2012-09-11
Good job!

After further investigation with gdell, we could clearly point out that the RAID is [correctly activated by Ubuntu 12.04]("http://paste.ubuntu.com/1198530/"), but [not by Boot-Repair-Disk]("http://paste.ubuntu.com/1198511/"). This shows that the problem comes from the old RAID drivers contained in Debian stable (on which Boot-Repair-Disk is based).

So RAID users have to use Boot-Repair on a recent Ubuntu disk instead of Boot-Repair-Disk. I will try to add a warning directly inside B-R. 

Thank you very much for your feedback gdell ! :)

---

### Post by YannBuntu on 2012-09-21
FYI, Boot-Repair-Disk will now suggest the user to use Boot-Repair from a Ubuntu-Secure disk when RAID is detected.

---

