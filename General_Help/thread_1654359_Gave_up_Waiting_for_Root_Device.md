---
title: "Gave up Waiting for Root Device"
date: 2010-12-28
forum: General Help
---

### Post by rafiwiener on 2010-12-28
hi i'm new to linux and i have a dell server T5400 with two HD 1Tb each. i did raid 0 and tried to install ubuntu server i got this command line saying Gave up Waiting for...
i googled and i found a link to this script 
bootinfoscript.sourceforge.net
i run and got this result
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 512 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.
 => Syslinux is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/mapper/isw_ccfciecagj_Volume0 and 
    looks at sector 512 of the same hard drive for core.img, but core.img can 
    not be found at this location.

sda1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

isw_ccfciecagj_Volume01: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_ccfciecagj_Volume02: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ccfciecagj_Volume03: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,039,743 3,907,039,743  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1             512         2,047         1,536 Bios Boot Partition
/dev/sda2           2,048 3,749,037,055 3,749,035,008 Linux or Data
/dev/sda3   3,749,037,056 3,907,039,231   158,002,176 Linux Swap

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda
Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             44    15,679,439    15,679,396   b W95 FAT32


Drive: isw_ccfciecagj_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_ccfciecagj_Volume0: 2000.4 GB, 2000404348928 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907039744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_ccfciecagj_Volume01                  1 3,907,039,743 3,907,039,743  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/mapper/isw_ccfciecagj_Volume01            512         2,047         1,536 Bios Boot Partition
/dev/mapper/isw_ccfciecagj_Volume02          2,048 3,749,037,055 3,749,035,008 Linux or Data
/dev/mapper/isw_ccfciecagj_Volume03  3,749,037,056 3,907,039,231   158,002,176 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_ccfciecagj_Volume0: PTTYPE="gpt" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc1        7822-4045                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/mapper/isw_ccfciecagj_Volume01: No such file or directory
error: /dev/mapper/isw_ccfciecagj_Volume02: No such file or directory
error: /dev/mapper/isw_ccfciecagj_Volume03: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_ccfciecagj_Volume0

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Install Ubuntu Server" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet --
	initrd	/install/initrd.gz
}
menuentry "Install in expert mode" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed priority=low --
	initrd	/install/initrd.gz
}
menuentry "Install Ubuntu Enterprise Cloud" {
	set gfxpayload=keep
	linux	/install/vmlinuz  file=/cdrom/preseed/cloud.seed quiet --
	initrd	/install/initrd.gz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/install/vmlinuz  MENU=/bin/cdrom-checker-menu quiet --
	initrd	/install/initrd.gz
}
menuentry "Rescue a broken system" {
	set gfxpayload=keep
	linux	/install/vmlinuz  rescue/enable=true --
	initrd	/install/initrd.gz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 20 00  |.X.SYSLINUX..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 2c 00 00 00  |........?...,...|
00000020  a4 3f ef 00 7a 07 00 00  00 00 00 00 02 00 00 00  |.?..z...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 45 40 22 78 4e  4f 20 4e 41 4d 45 20 20  |..)E@"xNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 54 24 40 00  66 ba 00 00 00 00 bb 00  |}.f.T$@.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on isw_ccfciecagj_Volume01


Unknown BootLoader  on isw_ccfciecagj_Volume02


Unknown BootLoader  on isw_ccfciecagj_Volume03



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume01: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume01: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume02: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume02: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume03: No such file or directory
hexdump: /dev/mapper/isw_ccfciecagj_Volume03: No such file or directory

```
if anyone please help me
i must say i tried ti install an edition of ubntu called bio-linux witch is based on the regular ubuntu edition but after the insallation nothing happend

---

