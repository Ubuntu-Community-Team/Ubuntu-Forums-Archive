---
title: "Kubuntu 10.10/Windows 7 dual boot problem"
date: 2012-07-22
forum: General Help
---

### Post by Afiorentino on 2012-07-22
I recently reinstalled Kubuntu 10.10 64bit on my spare hard drive, intending to be able to dual boot in to Windows 7 64bit. 

I've run in to a few problems now though:

I can't boot in to windows 7 now using the windows boot manager. Using the repair/recovery options from the windows recovery disk result in nothing.

Update-grub can't detect my windows partition.

Here is my boot info

```
                 Boot Info Script 0.60-git      [23 Feb 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /boot/bcd /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 Data partition (Windows/Linux)
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   625,141,759   624,672,768 EFI System partition

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0E3B-BBC9                              vfat       
/dev/sda3        EE244C61244C2EC1                       ntfs       
/dev/sdb1        2A402195402168B1                       ntfs       SEA_DISC

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /media/disk              squashfs   (ro,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/0E3B-BBC9         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /media/SEA_DISC          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /live/image              iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 b5 dc 6d a7  d0 53 00 00 00 00 00 01  |......m..S......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 8a a1 12 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[9805]) leaked on lvscan invocation. Parent PID 9743: bash
File descriptor 8 (pipe:[9805]) leaked on lvscan invocation. Parent PID 9743: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-07-22__01h30 ****************
boot-repair version : 3.16-0ppa10~lucid
boot-sav version : 3.17-0ppa18~lucid
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: no-internet
File descriptor 7 (pipe:[9805]) leaked on lvs invocation. Parent PID 7448: /bin/sh
File descriptor 8 (pipe:[9805]) leaked on lvs invocation. Parent PID 7448: /bin/sh
No volume groups found
LIVESESSION is : yes (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , x86_64  )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdb) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:


BLKID:
/dev/sda1: UUID="0E3B-BBC9" TYPE="vfat"
/dev/sda3: UUID="EE244C61244C2EC1" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"
/dev/sdb1: LABEL="SEA_DISC" UUID="2A402195402168B1" TYPE="ntfs"


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

LIST_GPTPART[1] is 1 (sda1 , sdb)
ReadEFI: /dev/sda , N 128 , 0 ,  , PRStart 1024 , PRSize 128
part /dev/sda1 is notBISEFI
part /dev/sda3 is BISEFI
TABLE_TYPE of sda is EFI
TABLE_TYPE of sdb is MSDos
sda1 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /media/0E3B-BBC9, no-os, gpt, notBISEFI, no-fstab.
sda3 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda3, no-os, no-gpt, BISEFI, no-fstab.
sdb1 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /media/SEA_DISC, no-os, no-gpt, notEFItable, no-fstab.

PARTED:

Model: ATA ST3320620AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
1      1049kB  106MB  105MB  fat32        EFI system partition
2      106MB   240MB  134MB               Microsoft reserved partition  msftres
3      240MB   320GB  320GB  ntfs         Basic data partition          boot


Model: Seagate External Drive (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  160GB  160GB  primary  ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


MOUNT:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /media/0E3B-BBC9 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/loop0 on /media/disk type squashfs (ro,nosuid,nodev,uhelper=udisks)
/dev/sdb1 on /media/SEA_DISC type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)


/sys/block/sda:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dvd dvdrw fd full fuse hidraw0 hidraw1 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usb vga_arbiter xconsole zero

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    7.9G   11M  7.9G   1% /
tmpfs        tmpfs    7.9G     0  7.9G   0% /lib/init/rw
udev         tmpfs    7.9G  228K  7.9G   1% /dev
tmpfs        tmpfs    7.9G     0  7.9G   0% /dev/shm
/dev/sr0   iso9660    339M  339M     0 100% /live/image
tmpfs        tmpfs    7.9G   11M  7.9G   1% /live/cow
tmpfs        tmpfs    7.9G     0  7.9G   0% /live
tmpfs        tmpfs    7.9G   68K  7.9G   1% /tmp
/dev/sda1     vfat     96M   19M   78M  20% /media/0E3B-BBC9
/dev/loop0
squashfs    313M  313M     0 100% /media/disk
/dev/sdb1  fuseblk    150G   22G  128G  15% /media/SEA_DISC
/dev/sda3  fuseblk    298G  265G   34G  89% /mnt/boot-sav/sda3

FDISK:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a6651cd

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000053d0

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321    7  HPFS/NTFS



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sdb1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sdb1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 2)
Will restore the MBR_TO_RESTORE : sda (mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
bootflag_action sda3 (=sda3)
parted /dev/sda set 1 boot off

                                                                          
Information: You may need to update /etc/fstab.

parted /dev/sda set 2 boot off

                                                                          
Information: You may need to update /etc/fstab.

parted /dev/sda set 4 boot off

                                                                          
Error: Partition doesn't exist.
parted /dev/sda set 3 boot on

                                                                          
Information: You may need to update /etc/fstab.

internet: no-internet
internet: no-internet

```

Thanks in advance

---

### Post by Bucky Ball on 2012-07-22
Looks like you installed grub to sdb and the machine was booting from there. When you killed Kubuntu you  killed grub. Your Windows is still there with boot fine. Perhaps you  could try getting into the BIOS and changing your first boot device to  whichever HDD is sda and that might do it ... think you could be booting (or trying to) from sdb at the moment but that looks empty. 

Good luck. ;)

---

### Post by oldfred on 2012-07-22
Is this a UEFI system?

You are showing gpt partitioning on sda, and Windows only boots with gpt partitions if in UEFI mode. Then the first partition has to be the efi partition, formated FAT32, and in gparted will show the boot flag.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

You have "boot flag" on sda3 now so it thinks it is the efi partition. In MBR you would have the boot flag on sda3 (or maybe sda2 if a 100MB boot partition). You also show the Microsoft reserved partition as sda2 which is for Microsoft in gpt partitions for extra code of some sort.

If a UEFI system I would not try any older Ubuntu's. Grub2 is still fixing UEFI issues & you want the newest version of grub2 with UEFI. You may be able to boot sdb in BIOS/MBR with sda in UEFI/gpt but I am not sure as you have to do that thru your UEFI somehow. 

Your Windows efi boot files may be in efi partition. I thought script showed them, but it does not now. Boot-Repair adds some info in its BootInfo report and will show them if there.

---

### Post by gordintoronto on 2012-07-22
As Oldfred said, you should avoid old versions. Kubuntu 10.10 has been unsupported for several months.

---

### Post by Afiorentino on 2012-07-22
Manually selecting my Windows partition to boot from my BIOS results in an OS error, stating that it cannot be found. 

I will do a distro upgrade tomorrow, download the latest version of boot repair and get back to you with my results.

---

