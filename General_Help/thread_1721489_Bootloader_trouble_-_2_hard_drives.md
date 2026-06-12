---
title: "Bootloader trouble - 2 hard drives"
date: 2011-04-04
forum: General Help
---

### Post by lukster91 on 2011-04-04
Hey,


Right. I have two hard drives. I have Windows 7 Home premium 64-bit SP1 on one hard drive and Ubuntu 10.10 installed on the other.

Although the installation was successful, Ubuntu on the other Hard drive didn't boot.

My problem is that I installed the bootloader on my Ubuntu hard drive, and as a result, I cannot boot into Windows without my Ubuntu hard drive plugged in.

I was testing the OS, and in long-term don't want this **old hard drive** which Ubuntu is installed on. However without it, I now can't boot into windows.

Can someone please tell me how I can fix it so that I can just have my windows HDD plugged in, and not my Ubuntu one, and so I can still get it to boot into windows?

Ideally I need to return it back to the status both hard drives were before the instalation.

Thank you very much in advance,

Luke Bellamy



Here is my system information: 
------------------
System Information
------------------
Time of this report: 4/4/2011, 21:14:49
       Machine name: v3u92
   Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_rtm.101119-1850)
           Language: English (Regional Setting: English)
System Manufacturer: System manufacturer
       System Model: System Product Name
               BIOS: BIOS Date: 02/24/10 16:41:12 Ver: 08.00.15
          Processor: Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz (4 CPUs), ~2.9GHz
             Memory: 4096MB RAM
Available OS Memory: 3966MB RAM
          Page File: 1845MB used, 6084MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
     DxDiag Version: 6.01.7601.17514 32bit Unicode

---

### Post by wilee-nilee on 2011-04-04
Sounds like you installed the grub bootloader to the mbr of the windows setup. So lets get this done to make it easier, click on the bootscript in my sig, run it with both HD's plugged in. Come back to the thread open a reply click on the **(#)** in the reply panel and paste al the text from the generated file in between the code tags.

Also let us know what discs you have like a recovery or install for W7 and a equal to the Ubuntu install disc.

---

### Post by lukster91 on 2011-04-04
> **wilee-nilee said:**
> Sounds like you installed the grub bootloader to the mbr of the windows setup. So lets get this done to make it easier, click on the bootscript in my sig, run it with both HD's plugged in. Come back to the thread open a reply click on the **(#)** in the reply panel and paste al the text from the generated file in between the code tags.

Also let us know what discs you have like a recovery or install for W7 and a equal to the Ubuntu install disc.

No windows 7 recovery disks as far as I am aware. I built this system myself, and I installed the WIN7 OS using an OEM disk. 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   563,116,031   563,113,984  83 Linux
/dev/sdb2         563,118,078   586,113,023    22,994,946   5 Extended
/dev/sdb5         563,118,080   586,113,023    22,994,944  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4047 MB, 4047503360 bytes
125 heads, 62 sectors/track, 1020 cylinders, total 7905280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     7,904,999     7,904,938   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        46F49ABDF49AAEA5                       ntfs       System Reserved               
/dev/sda2        0EF89C48F89C3047                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c037da4d-4f6b-45bf-93fe-9c8d6e2dea53   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        d3e6d0cd-3fee-4b91-ad80-ac540a4ca13d   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1CAF-A88D                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c037da4d-4f6b-45bf-93fe-9c8d6e2dea53
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c037da4d-4f6b-45bf-93fe-9c8d6e2dea53
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c037da4d-4f6b-45bf-93fe-9c8d6e2dea53
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c037da4d-4f6b-45bf-93fe-9c8d6e2dea53 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c037da4d-4f6b-45bf-93fe-9c8d6e2dea53
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c037da4d-4f6b-45bf-93fe-9c8d6e2dea53 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c037da4d-4f6b-45bf-93fe-9c8d6e2dea53
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c037da4d-4f6b-45bf-93fe-9c8d6e2dea53
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 46f49abdf49aaea5
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d3e6d0cd-3fee-4b91-ad80-ac540a4ca13d none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  66.7GB: boot/grub/core.img
  64.5GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic
  66.7GB: boot/vmlinuz-2.6.35-22-generic
   1.0GB: initrd.img
  66.7GB: vmlinuz

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

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  04 8b 54 03 0c c1 e1 04  89 54 0b 0c 8b 46 10 8b  |..T......T...F..|
00000010  9e dc b2 00 00 8b 8e 80  b6 00 00 c1 e0 04 8b 14  |................|
00000020  03 c1 e1 04 89 14 0b 8b  46 10 8b 9e dc b2 00 00  |........F.......|
00000030  8b 8e 80 b6 00 00 c1 e0  04 8b 54 03 04 c1 e1 04  |..........T.....|
00000040  89 54 0b 04 8b 46 10 8b  9e dc b2 00 00 8b 8e 80  |.T...F..........|
00000050  b6 00 00 c1 e0 04 8b 54  03 08 c1 e1 04 89 54 0b  |.......T......T.|
00000060  08 8b 46 10 8b 9e dc b2  00 00 8b 8e 80 b6 00 00  |..F.............|
00000070  c1 e0 04 8b 54 03 0c c1  e1 04 89 54 0b 0c 8b 46  |....T......T...F|
00000080  10 8b 9e e0 b2 00 00 8b  8e 80 b6 00 00 c1 e0 04  |................|
00000090  8b 14 03 c1 e1 04 89 14  0b 8b 46 10 8b 9e e0 b2  |..........F.....|
000000a0  00 00 8b 8e 80 b6 00 00  c1 e0 04 8b 54 03 04 c1  |............T...|
000000b0  e1 04 89 54 0b 04 8b 46  10 8b 9e e0 b2 00 00 8b  |...T...F........|
000000c0  8e 80 b6 00 00 c1 e0 04  8b 54 03 08 c1 e1 04 89  |.........T......|
000000d0  54 0b 08 8b 46 10 8b 9e  e0 b2 00 00 8b 8e 80 b6  |T...F...........|
000000e0  00 00 c1 e0 04 8b 54 03  0c c1 e1 04 89 54 0b 0c  |......T......T..|
000000f0  8b 46 10 8b 9e e4 b2 00  00 8b 8e 80 b6 00 00 c1  |.F..............|
00000100  e0 04 8b 14 03 c1 e1 04  89 14 0b 8b 46 10 8b 9e  |............F...|
00000110  e4 b2 00 00 8b 8e 80 b6  00 00 c1 e0 04 8b 54 03  |..............T.|
00000120  04 c1 e1 04 89 54 0b 04  8b 46 10 8b 9e e4 b2 00  |.....T...F......|
00000130  00 8b 8e 80 b6 00 00 c1  e0 04 8b 54 03 08 c1 e1  |...........T....|
00000140  04 89 54 0b 08 8b 46 10  8b 9e e4 b2 00 00 8b 8e  |..T...F.........|
00000150  80 b6 00 00 c1 e0 04 8b  54 03 0c c1 e1 04 89 54  |........T......T|
00000160  0b 0c 8b 9e ec b2 00 00  8b 46 10 8b 96 80 b6 00  |.........F......|
00000170  00 8b 0c 83 89 0c 93 89  f6 8d bc 27 00 00 00 00  |...........'....|
00000180  ff 86 80 b6 00 00 31 db  89 9e f8 b5 00 00 8b 46  |......1........F|
00000190  0c 8b 8e 34 b6 00 00 89  3c 24 ff 14 81 31 f6 89  |...4....<$...1..|
000001a0  b7 d4 00 00 00 e9 10 f5  ff ff 8d b6 00 00 00 00  |................|
000001b0  ff 15 0c 00 00 00 e9 e1  f4 ff ff 90 8d 74 00 fe  |.............t..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e0 5e 01 00 00  |............^...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 d0 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  aa 9e 78 00 18 1e 00 00  00 00 00 00 02 00 00 00  |..x.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 8d a8 af 1c 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
00000100  7d 00 66 b8 78 f7 15 00  66 ba 00 00 00 00 bb 00  |}.f.x...f.......|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

Thanks for this!

---

### Post by lukster91 on 2011-04-04
P.S. Using a LiveCD currently if that makes any difference!

---

### Post by wilee-nilee on 2011-04-04
Easy fix down load this W7 recovery disc and run the single command to reload the MS bootloader in the sda mbr.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr **
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Then put the sdb HD first in the bios to be read, and from the live cd follow this link to load grub2 to the mbr of sdb.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

So now if you do these things if you have the sda first in the bios it will go straight to windows, if you have the sdb first you will get the grub menu, and a choice of either OS.

---

### Post by lukster91 on 2011-04-05
Thank you. Your efforts have worked. I can now boot into windows with the windows HDD selected in the BIOS.

Thank you very much!

---

