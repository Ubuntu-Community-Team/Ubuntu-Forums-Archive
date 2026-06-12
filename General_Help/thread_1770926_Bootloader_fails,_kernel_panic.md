---
title: "Bootloader fails, kernel panic"
date: 2011-05-29
forum: General Help
---

### Post by jake.anq on 2011-05-29
I recently decided to upgrade a clean install of Ubuntu Maverick to Natty and also upgrade to 64-bit.
On booting, the computer displays:
error: no such device: 33ed8023-ddb7-44fa-8d1a-bb6050b2d08b.
grub rescue>
When booting from a Super Grub2 disk, FreeBSD boots fine, Windows XP boots fine but Fedora and Ubuntu both fail with the same message:
Kernel Panic - not syncing: VFS: Unable to mount root fr on unknown-block(0,0)
Pid:1, comm: swapper Not tainted 2.6.35.6-45.fc14.i686 #1
Call Trace:
[<c07a56b9>] ? printk+0x25/0x2c
[<c07a561e>] panic+0x50.0xc6
[<c0a1dcba>] mount_block_root+0x1ee/0x20e
[<c04e494a>] ? sys_mknod+0x18/0x1a
[<c0a1ddfe>] mount_root+0x4c/0x54
[<c0a1df4b>] prepare_namespace+0x145/0x176
[<c0a1da09>] kernel_init+0x22d/0x23c
[<c0a1d7dc>] ? kernel_init+0x0/0x23c
[<c04038fe>] kernel_thread_helper+0x6/0x10

Output from Boot Info script:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file 
                       /super_grub_disk_hybrid-1.98s1.iso looks at sector 1 
                       of the same hard drive for core.img. core.img is at 
                       this location and looks in partition 256 for 
                       /boot/grub/i386-pc.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......(......0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1418472 of /dev/sde1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sde1 starts at sector 
                       0. But according to the info from fdisk, sde1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    71,682,029    71,681,967   7 NTFS / exFAT / HPFS
/dev/sda2    *     71,682,048   156,301,311    84,619,264  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   195,311,615   195,309,568  83 Linux
/dev/sdb2       1,945,712,638 1,953,523,711     7,811,074   5 Extended
/dev/sdb5       1,945,712,640 1,953,523,711     7,811,072  82 Linux swap / Solaris
/dev/sdb3         386,041,856 1,945,710,591 1,559,668,736  83 Linux
/dev/sdb4         195,311,616   386,041,823   190,730,208  a5 FreeBSD


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   976,773,119   976,771,072  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 16.0 GB, 16039018496 bytes
75 heads, 40 sectors/track, 10442 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             40    31,326,207    31,326,168   c W95 FAT32 (LBA)


Drive: sde _____________________________________________________________________

Disk /dev/sde: 4025 MB, 4025810432 bytes
124 heads, 62 sectors/track, 1022 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             62     7,857,135     7,857,074   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       a0d31e4e-61c7-4f16-9f93-a96a5178c8f8   ext3       
/dev/sda1        72107EC3107E8E3B                       ntfs       
/dev/sda2        e2aa733d-bef3-4397-9ab1-8276666da7b2   ext4       _Fedora-14-i686-
/dev/sdb1        f6fcb254-849b-4379-9b81-a0c1cd67e2cb   xfs        
/dev/sdb3        560b5777-9720-490d-9b10-8625ff18a887   ext4       
/dev/sdb5        8f1a520f-d0a1-4cf4-b1a9-27c27ad72870   swap       
/dev/sdb6                                               ufs        
/dev/sdc1        323659f7-15ee-4a9a-aecb-b5110cda41c6   ext4       
/dev/sdd1        E7CB-72F6                              vfat       Lexar
/dev/sde1        C50D-51F6                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/323659f7-15ee-4a9a-aecb-b5110cda41c6 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/Lexar             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sde1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Wed Apr 13 10:02:53 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=e2aa733d-bef3-4397-9ab1-8276666da7b2 /                       ext4    defaults        1 1
UUID=8f1a520f-d0a1-4cf4-b1a9-27c27ad72870 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  36.186725616 = 38.855200768   boot/initramfs-2.6.35.6-45.fc14.i686.img       2
  35.230670929 = 37.828644864   boot/initrd-plymouth.img                       1
  35.209224701 = 37.805617152   boot/vmlinuz-2.6.35.6-45.fc14.i686             1

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=f6fcb254-849b-4379-9b81-a0c1cd67e2cb /               xfs     defaults        0       1
# swap was on /dev/sdb5 during installation
UUID=8f1a520f-d0a1-4cf4-b1a9-27c27ad72870 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  47.264621735 = 50.750001152   boot/vmlinuz-2.6.38-8-generic                  1
  47.264621735 = 50.750001152   vmlinuz                                        1

========================= sde1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sde1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sde1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb4

00000000  eb 3c 00 00 00 00 00 00  00 00 00 00 02 00 00 00  |.<..............|
00000010  00 00 00 00 00 00 00 00  12 00 02 00 00 00 00 00  |................|
00000020  00 00 00 00 00 16 1f 66  6a 00 51 50 06 53 31 c0  |.......fj.QP.S1.|
00000030  88 f0 50 6a 10 89 e5 e8  c0 00 8d 66 10 cb fc 31  |..Pj.......f...1|
00000040  c9 8e c1 8e d9 8e d1 bc  00 7c 89 e6 bf 00 07 fe  |.........|......|
00000050  c5 f3 a5 be ee 7d 80 fa  80 72 2c b6 01 e8 60 00  |.....}...r,...`.|
00000060  b9 01 00 be be 8d b6 01  80 7c 04 a5 75 07 e3 19  |.........|..u...|
00000070  f6 04 80 75 14 83 c6 10  fe c6 80 fe 05 72 e9 49  |...u.........r.I|
00000080  e3 e1 be a2 7d eb 4b 31  d2 89 16 00 09 b6 10 e8  |....}.K1........|
00000090  2e 00 bb 00 90 8b 77 0a  01 de bf 00 c0 b9 00 ae  |......w.........|
000000a0  29 f1 f3 a4 fa 49 74 14  e4 64 a8 02 75 f7 b0 d1  |)....It..d..u...|
000000b0  e6 64 e4 64 a8 02 75 fa  b0 df e6 60 fb e9 50 13  |.d.d..u....`..P.|
000000c0  bb 00 8c 8b 44 08 8b 4c  0a 0e e8 5a ff 73 2a be  |....D..L...Z.s*.|
000000d0  9d 7d e8 1c 00 be a7 7d  e8 16 00 30 e4 cd 16 c7  |.}.....}...0....|
000000e0  06 72 04 34 12 ea f0 ff  00 f0 bb 07 00 b4 0e cd  |.r.4............|
000000f0  10 ac 84 c0 75 f4 b4 01  f9 c3 2e f6 06 b0 08 80  |....u...........|
00000100  74 22 80 fa 80 72 1d bb  aa 55 52 b4 41 cd 13 5a  |t"...r...UR.A..Z|
00000110  72 12 81 fb 55 aa 75 0c  f6 c1 01 74 07 89 ee b4  |r...U.u....t....|
00000120  42 cd 13 c3 52 b4 08 cd  13 88 f5 5a 72 cb 80 e1  |B...R......Zr...|
00000130  3f 74 c3 fa 66 8b 46 08  52 66 0f b6 d9 66 31 d2  |?t..f.F.Rf...f1.|
00000140  66 f7 f3 88 eb 88 d5 43  30 d2 66 f7 f3 88 d7 5a  |f......C0.f....Z|
00000150  66 3d ff 03 00 00 fb 77  9d 86 c4 c0 c8 02 08 e8  |f=.....w........|
00000160  40 91 88 fe 28 e0 8a 66  02 38 e0 72 02 b0 01 bf  |@...(..f.8.r....|
00000170  05 00 c4 5e 04 50 b4 02  cd 13 5b 73 0a 4f 74 1c  |...^.P....[s.Ot.|
00000180  30 e4 cd 13 93 eb eb 0f  b6 c3 01 46 08 73 03 ff  |0..........F.s..|
00000190  46 0a d0 e3 00 5e 05 28  46 02 77 88 c3 52 65 61  |F....^.(F.w..Rea|
000001a0  64 00 42 6f 6f 74 00 20  65 72 72 6f 72 0d 0a 00  |d.Boot. error...|
000001b0  80 90 90 90 90 90 90 90  90 90 90 90 90 90 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001f0  01 00 a5 fe ff ff 00 00  00 00 50 c3 00 00 55 aa  |..........P...U.|
00000200


=============================== StdErr Messages: ===============================

./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```The unknown partition is FreeBSD and sdd and sde are 2 unrelated USB devices I used to run the bootinfo script.  Fedora is installed on sda2 and Ubuntu on sdb1.

Any help would be appreciated
Thanks

---

### Post by drs305 on 2011-05-29
It doesn't appear you have the grub files on sdb1 unless there is an issue with the boot info script and xfs (which I've never used). Assuming the script is correct, this can be fixed from a Natty LiveCD by mounting sdb1 and installing grub:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdb
```

Don't use the partition number in the second command and make sure the BIOS boots sdb first.*

* However it looks like you have a more pressing problem. The boot info script didn't find an initrd file in sdb1's /boot folder.  If it really doesn't exist, you will need to create one.

You can do this from the LiveCD as well, but you will have to chroot into sdb1 from a Natty CD and run the *mkinitramfs*n or *update-initramfs* command to create the initrd.img file. You can follow the instructions in the "Chroot" link in my signature line to chroot into your real installation.

---

### Post by jake.anq on 2011-06-13
Hi

Thanks for the help, I now have all of the operating systems working except Ubuntu.  The error appears when grub tries to boot Ubuntu and it is
```
error: cannot read the Linux header
error: you need to load the kernel first

Press any key to continue...
```Thanks again

---

### Post by oldfred on 2011-06-14
I would follow drs305's instructions to chroot into your Ubuntu and run a full set of updates and install grub2 & a new kernel.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
#do not think you have to uninstall grub but a total reinstall of grub2 would be good:
# uninstall both grub legacy & grub2 reinstall grub2 and to sdb
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sdb
grub-install --recheck /dev/sdb

#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

---

### Post by jake.anq on 2011-06-23
Hi

I managed to find the problem.  Grub did not like the XFS partition that I had installed it on.
 Thanks for the help.

---

