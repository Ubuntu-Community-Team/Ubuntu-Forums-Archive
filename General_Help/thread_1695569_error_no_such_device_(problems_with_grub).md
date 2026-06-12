---
title: "error no such device (problems with grub)"
date: 2011-02-26
forum: General Help
---

### Post by cyberboy109 on 2011-02-26
im running ubuntu 10.10 64bit and last night i decide to install lubuntu on a seprate hard drive
one  finished and restarted to ubuntu i got the error no such device 
so i got my ubuntu disk and used the terminal 
sudo fdisk -l

and i got 
disk /dev/sde: 160.0gb,160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

    device boot  start  end    blocks     id   system
/dev/sde1    *       1  18663  149903360   83  linux
/dev/sde2        18663  19458  6384641      5  extended
/dev/sde5        18663  19458  6384640     82  linux swap / soloris

so i type

sudo mkdir /media/sde5
sudo mount /dev/sde5 /media/sde5

and i get this

/dev/sde5 looks like swapspace -not mounted
mount: you must specify the filesystem types


I used a guide but i must be doing summit wrong im still new

if i plug in the lubuntu external hardrive i can boot into my ubuntu 10.10

---

### Post by amsterdamharu on 2011-02-26
Could you start Ubuntu live CD/usb and download the boot info script?
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Copy it to your Desktop (it usually is in Downloads).
Run the following commands:
```
cd ~/Desktop
sudo bash boot_info_script*
```
To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
There should be a file on your Desktop named RESULTS.txt please post the content of this file here too using &#91;code]Your pasted stuff&#91;/code]

Please run it with the usb drive plugged in so we can see info on all drives involved.

I think you installed grub on sda's mbr and the rest of the files on the usb disk. When grub starts it looks on the usb disk for the rest of the files to boot. So it'll only work when usb is plugged in. This can be solved by re installing grub files in the right partition on your local drive so its always available even when the usb drive is not plugged in.

---

### Post by cyberboy109 on 2011-02-26
sorry for the long reply was just backing up data

here we go


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub  is installed in the MBR of /dev/sdb and looks at sector 34052 on 
    boot drive #1 for the stage2 file, but no stage2 files can be found at 
    this location.
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   299,808,767   299,806,720  83 Linux
/dev/sda2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sda5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   156,296,384   156,296,322   b W95 FAT32


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8168 MB, 8168931328 bytes
252 heads, 62 sectors/track, 1021 cylinders, total 15954944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             62    15,952,103    15,952,042   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ce36a3d9-cff7-41f8-98b7-1c159505bc9b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        90306405-79fb-4927-83e3-c76d73261dce   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E0C1-93F2                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sde1        CDBE-A566                              vfat       New Volume                    
/dev/sde: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sde1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=ce36a3d9-cff7-41f8-98b7-1c159505bc9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=ce36a3d9-cff7-41f8-98b7-1c159505bc9b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ce36a3d9-cff7-41f8-98b7-1c159505bc9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ce36a3d9-cff7-41f8-98b7-1c159505bc9b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ce36a3d9-cff7-41f8-98b7-1c159505bc9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ce36a3d9-cff7-41f8-98b7-1c159505bc9b ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ce36a3d9-cff7-41f8-98b7-1c159505bc9b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ce36a3d9-cff7-41f8-98b7-1c159505bc9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=90306405-79fb-4927-83e3-c76d73261dce none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 137.5GB: boot/grub/core.img
  82.0GB: boot/grub/grub.cfg
   2.0GB: boot/initrd.img-2.6.35-22-generic
   1.8GB: boot/initrd.img-2.6.35-25-generic
  48.3GB: boot/initrd.img-2.6.35-27-generic
 137.5GB: boot/vmlinuz-2.6.35-22-generic
 137.5GB: boot/vmlinuz-2.6.35-25-generic
 137.5GB: boot/vmlinuz-2.6.35-27-generic
  48.3GB: initrd.img
   1.8GB: initrd.img.old
 137.5GB: vmlinuz
 137.5GB: vmlinuz.old

=========================== sde1/boot/grub/grub.cfg: ===========================


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

=================== sde1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ce e0 31 19 78 fc 03 a0  f9 54 99 3b e4 22 b0 6a  |..1.x....T.;.".j|
00000010  01 ed 64 05 29 72 59 be  78 07 aa 8a 7d 3d 5b 73  |..d.)rY.x...}=[s|
00000020  8f 82 1c 36 36 41 45 df  55 39 ff fb f5 42 1a 48  |...66AE.U9...B.H|
00000030  01 8a 80 3d 52 b0 86 a0  79 e5 37 de aa a4 95 4f  |...=R...y.7....O|
00000040  95 58 d0 fe c6 b2 8c b6  a8 ff aa bf 7a a8 ac 99  |.X..........z...|
00000050  06 f0 92 0c 3d a1 04 b8  bf c5 e3 e1 e7 e5 95 ae  |....=...........|
00000060  94 91 1e 02 99 fe 74 7b  e8 ac 7d 6a a5 16 55 73  |......t{..}j..Us|
00000070  3d fb 25 1e 08 97 df 66  98 12 84 ab 7e a9 5a b0  |=.%....f....~.Z.|
00000080  33 07 dc 63 15 c0 09 12  47 c2 58 30 28 44 aa 5d  |3..c....G.X0(D.]|
00000090  55 fb e3 aa 5f 27 37 4b  a3 3c 6f 10 92 80 70 06  |U..._'7K.<o...p.|
000000a0  4b e2 e5 65 ca 65 1e 7d  54 ad 35 94 02 0f d7 11  |K..e.e.}T.5.....|
000000b0  d5 2f 8a 79 12 d3 fe 56  ae 58 a7 24 e7 81 90 68  |./.y...V.X.$...h|
000000c0  c6 5d fe 29 62 02 b6 bc  1a 04 31 f5 12 44 8f 8f  |.].)b.....1..D..|
000000d0  b3 aa 7d db 72 ca ab e3  da 8c 89 34 c7 ed d2 ef  |..}.r......4....|
000000e0  a7 c1 0c 94 1b e0 82 01  d5 54 12 8b c4 41 f8 fa  |.........T...A..|
000000f0  59 08 4b fd e1 d5 8d e7  c7 a9 63 c1 a8 f6 51 f2  |Y.K.......c...Q.|
00000100  a5 45 fd 04 2c 2e 55 dd  aa 3a a4 b5 e0 a6 57 f1  |.E..,.U..:....W.|
00000110  2a 4b ea cb 6d a2 64 2a  f2 bf d8 ad 4f 2c 55 9d  |*K..m.d*....O,U.|
00000120  ec 53 04 6e 24 42 88 e8  f6 52 c7 97 7a db fb dc  |.S.n$B...R..z...|
00000130  ac 56 20 b1 e0 a6 7c d9  77 84 4a 3d 25 e7 33 b7  |.V ...|.w.J=%.3.|
00000140  fd 04 57 55 6d 86 73 c3  b5 74 bb d5 9d fd 4b f0  |..WUm.s..t....K.|
00000150  b1 e0 87 9b c2 58 20 aa  55 69 75 51 22 8b fe a4  |.....X .UiuQ"...|
00000160  b0 2c 57 6f ae 7b d5 a3  80 c0 1e 0a 22 ef 0f 1b  |.,Wo.{......"...|
00000170  bc 03 9f e6 54 d8 35 f2  bb de 24 25 27 2f 9a e4  |....T.5...$%'/..|
00000180  2a 27 ff f7 a4 ed 16 ba  cd 03 34 32 4c 22 3e 12  |*'........42L">.|
00000190  15 41 d4 02 35 42 1e b4  2c f7 d5 c8 54 85 e2 42  |.A..5B..,...T..B|
000001a0  ad f2 ab 90 41 e1 e0 85  96 f5 5c ad 88 d8 4c 47  |....A.....\...LG|
000001b0  7d 65 ca ae 91 41 1b fb  e6 ca 45 9e d8 19 00 fe  |}e...A....E.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sde1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 fc 00 00 00 00 00  |........>.......|
00000020  aa 68 f3 00 c0 3c 00 00  00 00 00 00 02 00 00 00  |.h...<..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 66 a5 be cd 4e  65 77 20 56 6f 6c 75 6d  |..)f...New Volum|
00000050  65 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |e FAT32   ..1...|
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
00000100  7d 00 66 b8 50 ac 16 00  66 ba 00 00 00 00 bb 00  |}.f.P...f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e dd ca 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

sdc sdd sdf

---

### Post by amsterdamharu on 2011-02-26
[COLOR=Red]There should be a file on your Desktop named RESULTS.txt please post the  content of this file here too using &#91;code]Your pasted stuff&#91;/code]

[COLOR=Black]I don't have the time now to check the output of the boot info but maybe someone else will come along soon and give you some advice.

In the mean time you could try editing your previous post and make it more readable for others to go through the output.
[/COLOR][/COLOR]

---

### Post by ajgreeny on 2011-02-26
You seem to have got yourself into a spot of bother someway or another, don't you?

There is no sde5 at all according to the RESULTS.txt file, so how did you manage to find it in the **sudo fdisk -l** command?  Have you changed something in your setup?  The only partition with a number 5 is sda5 so I am wondering if your system is somehow confusing the disk name and you should be using sda5, not sde5.  Certainly the grub you should be using is grub2 on sda, and the config files for it are in sda1, which is quite normal in a system.  But you also have legacy grub on sdb, but that looks for config files which don't seem to exist.  Is this from an older linux install that no longer is on your system?

You will note that the RESULTS.txt file also notes the absence of sdb, sdc, and sdf, so I begin to think you may have added and removed disks at various times and the whole system is totally unsure what is what.  Which disk is, or which do you think is the boot device for the system, ie is first boot device set in the BIOS?  It looks as if it should be hd0 in your BIOS (or that is how my BIOS names disks), which is the equivalent of sda.  Making a change of that BIOS setting to hd0 may be all you need to get your system to boot.

If your system isn't unsure, I certainly am, so I await any more info you or any other poster can give, which might help me sort out the disk naming difficulties and where we go from here.

---

### Post by cyberboy109 on 2011-02-27
i got it fixed i was misreading the steps i found and was typing in the wrong sde

---

### Post by ajgreeny on 2011-02-28
Great!!

Just for reference, what had you read wrong, and what did you need to do to fix it all?  Was it just a change from sde to sda and the correct number at the end (sda5 was indeed swap) in the command you tried?

---

