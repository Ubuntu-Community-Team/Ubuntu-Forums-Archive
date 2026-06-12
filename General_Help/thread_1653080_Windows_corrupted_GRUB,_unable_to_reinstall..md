---
title: "Windows corrupted GRUB, unable to reinstall."
date: 2010-12-26
forum: General Help
---

### Post by mickliddy on 2010-12-26
Firstly, I'd just like to apologise since I am not 100% sure it this is in the correct place and I am pretty illiterate with Ubuntu. So, I am pretty new to Linux in general and decided to give Ubuntu a go alongside my Windows 7 install. However; for some reason Win7 has gone and run a startup repair (there was two boot options in GRUB, perhaps I chose the wrong one by accident) which has corrupted my GRUB. Now, the only way I can get anything to run is by booting Ubuntu of a live-pendrive/flashdrive!
I tried following a couple of walkthroughs that claimed to fix the problem; and I don't doubt that they work - on someone elses computer! I receive errors whenever I try to use things like 'sudo grub' and often (but not always) with 'mkdir' and 'mount' - and I have very little idea what some of them are doing (I gather 'mkdir' is making a directory and 'mount' is mounting a device virtually, but some others are a little harder to guess)
So, I am wondering if someone has a little insight as to how I can fix this and perhaps point me in the correct direction to learning about making my way around ubuntu and these fancy terminal commands! :)

Currently, I am at the stage where I can boot into my flash drive by spamming escape before the bootloader. However, when GRUB loads it tells me there is an error and gives me a command line; through which I have been unable to get anything to happen. I am running Ubuntu 10.10, I believe, and Windows 7 on the same hard-disk and possibly the same partition (though, I am unsure of how Ubuntu works itself into partition's). I also ran a little code (seemed somewhat like a batchfile in windows) that made a txt file of my boot info; I'm attaching it below if that helps at all.

Not sure what other information I can give that will be of use, but let me know if there is anything missing! Some help on this would be greatly appreciated; so a please and thanks in advanced!

Boot Info Results:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,716,280   274,904,279   244,188,000   7 HPFS/NTFS
/dev/sda3         274,904,341   976,768,064   701,863,724   f W95 Ext d (LBA)
/dev/sda5         274,904,343   807,378,704   532,474,362   7 HPFS/NTFS
/dev/sda6         807,378,768   889,269,368    81,890,601  83 Linux
/dev/sda7         889,270,272   966,383,615    77,113,344  83 Linux
/dev/sda8         966,385,664   969,779,199     3,393,536  82 Linux swap / Solaris
/dev/sda9         969,779,853   976,768,064     6,988,212  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 7958 MB, 7958691840 bytes
151 heads, 15 sectors/track, 6862 cylinders, total 15544320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,192    15,544,319    15,536,128   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        EE7C34277C33E94B                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        810C01CABB2D03B0                       ntfs       DATA                          
/dev/sda6        aceef6d0-d78b-4f00-b36f-19a62db90bb7   ext4                                     
/dev/sda7        ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3   ext4                                     
/dev/sda8        89a303a3-db86-43d8-927b-4f91fe1a4b5e   swap                                     
/dev/sda9        bbb099eb-aafc-43a4-b20f-68440492628d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        54DA20B6DA2095F0                       ntfs       Chimera                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8A07-A343                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Chimera           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set aceef6d0-d78b-4f00-b36f-19a62db90bb7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set aceef6d0-d78b-4f00-b36f-19a62db90bb7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=aceef6d0-d78b-4f00-b36f-19a62db90bb7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set aceef6d0-d78b-4f00-b36f-19a62db90bb7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=aceef6d0-d78b-4f00-b36f-19a62db90bb7 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set eef4e92af4e8f62d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=aceef6d0-d78b-4f00-b36f-19a62db90bb7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=bbb099eb-aafc-43a4-b20f-68440492628d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 413.5GB: boot/grub/core.img
 418.7GB: boot/grub/grub.cfg
 413.5GB: boot/initrd.img-2.6.31-14-generic
 413.5GB: boot/vmlinuz-2.6.31-14-generic
 413.5GB: initrd.img
 413.5GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3 ro single 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set aceef6d0-d78b-4f00-b36f-19a62db90bb7
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=aceef6d0-d78b-4f00-b36f-19a62db90bb7 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set aceef6d0-d78b-4f00-b36f-19a62db90bb7
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=aceef6d0-d78b-4f00-b36f-19a62db90bb7 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=ae36be3f-7fcc-4283-bb47-e1a44cc5f1f3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=89a303a3-db86-43d8-927b-4f91fe1a4b5e none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 472.6GB: boot/grub/core.img
 492.4GB: boot/grub/grub.cfg
 456.5GB: boot/initrd.img-2.6.35-22-generic
 472.6GB: boot/vmlinuz-2.6.35-22-generic
 456.5GB: initrd.img
 472.6GB: vmlinuz

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

Unknown BootLoader  on sda3

00000000  81 0e 00 00 82 0e 00 00  83 0e 00 00 84 0e 00 00  |................|
00000010  85 0e 00 00 86 0e 00 00  87 0e 00 00 88 0e 00 00  |................|
00000020  89 0e 00 00 8a 0e 00 00  8b 0e 00 00 8c 0e 00 00  |................|
00000030  8d 0e 00 00 8e 0e 00 00  8f 0e 00 00 90 0e 00 00  |................|
00000040  91 0e 00 00 92 0e 00 00  93 0e 00 00 94 0e 00 00  |................|
00000050  95 0e 00 00 96 0e 00 00  97 0e 00 00 98 0e 00 00  |................|
00000060  99 0e 00 00 9a 0e 00 00  9b 0e 00 00 9c 0e 00 00  |................|
00000070  9d 0e 00 00 9e 0e 00 00  9f 0e 00 00 a0 0e 00 00  |................|
00000080  a1 0e 00 00 a2 0e 00 00  a3 0e 00 00 a4 0e 00 00  |................|
00000090  a5 0e 00 00 a6 0e 00 00  a7 0e 00 00 a8 0e 00 00  |................|
000000a0  a9 0e 00 00 aa 0e 00 00  ab 0e 00 00 ac 0e 00 00  |................|
000000b0  ad 0e 00 00 ae 0e 00 00  af 0e 00 00 b0 0e 00 00  |................|
000000c0  b1 0e 00 00 b2 0e 00 00  b3 0e 00 00 b4 0e 00 00  |................|
000000d0  b5 0e 00 00 b6 0e 00 00  b7 0e 00 00 b8 0e 00 00  |................|
000000e0  b9 0e 00 00 ba 0e 00 00  bb 0e 00 00 bc 0e 00 00  |................|
000000f0  bd 0e 00 00 be 0e 00 00  bf 0e 00 00 c0 0e 00 00  |................|
00000100  c1 0e 00 00 c2 0e 00 00  c3 0e 00 00 c4 0e 00 00  |................|
00000110  c5 0e 00 00 c6 0e 00 00  c7 0e 00 00 c8 0e 00 00  |................|
00000120  c9 0e 00 00 ca 0e 00 00  cb 0e 00 00 cc 0e 00 00  |................|
00000130  cd 0e 00 00 ce 0e 00 00  cf 0e 00 00 d0 0e 00 00  |................|
00000140  d1 0e 00 00 d2 0e 00 00  d3 0e 00 00 d4 0e 00 00  |................|
00000150  d5 0e 00 00 d6 0e 00 00  d7 0e 00 00 d8 0e 00 00  |................|
00000160  d9 0e 00 00 da 0e 00 00  db 0e 00 00 dc 0e 00 00  |................|
00000170  dd 0e 00 00 de 0e 00 00  df 0e 00 00 e0 0e 00 00  |................|
00000180  e1 0e 00 00 e2 0e 00 00  e3 0e 00 00 e4 0e 00 00  |................|
00000190  e5 0e 00 00 e6 0e 00 00  e7 0e 00 00 e8 0e 00 00  |................|
000001a0  e9 0e 00 00 ea 0e 00 00  eb 0e 00 00 ec 0e 00 00  |................|
000001b0  ed 0e 00 00 ee 0e 00 00  ef 0e 00 00 f0 0e 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 fa e9 bc 1f 00 fe  |................|
000001d0  ff ff 05 fe ff ff fc e9  bc 1f 68 8d e1 04 00 00  |..........h.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 30 11  |.X.SYSLINUX..@0.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 00 00  |........?.... ..|
00000020  00 10 ed 00 68 07 00 00  00 00 00 00 02 00 00 00  |....h...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 43 a3 07 8a 4e  4f 20 4e 41 4d 45 20 20  |..)C...NO NAME  |
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
00000100  7d 00 66 b8 40 20 00 00  66 ba 00 00 00 00 bb 00  |}.f.@ ..f.......|
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


```

---

### Post by Quackers on 2010-12-26
There are one or two problems with the output of the boot script.
Grub is installed in the mbr of the first hard drive (sda) but it is looking for its boot files in sda8, when Ubuntu 9.10's boot files are in sda6 and Ubuntu 10.10's boot files are in sda7.
According to the boot script there is nothing installed on your 1TB disc (sdb).
The boot flag for Windows 7 has been moved to sda2, whereas the boot files for Windows 7 start in sda1.
I'll be back shortly :-)

---

### Post by Quackers on 2010-12-26
I suggest firstly that we re-install grub.
We can try the short way first, which I think will work ok.
From the Live cd/usb please open a terminal (Applications > Accessories > Terminal) and copy/paste these lines into it, one at a time, pressing enter after each one.
```
sudo mount /dev/sda7 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
```
If that reports no errors please reboot, taking the cd/usb out first.
Hopefully Ubuntu 10.10 will boot up directly.
If it does please come back and confirm before doing anything else.
If nothing boots please boot from the live cd/usb again and come back.

---

### Post by mickliddy on 2010-12-26
All hail Quackers! A massive thank-you; that has restored GRUB! What did each of those commands do, and what happened to GRUB in the first place?
Also, the GRUB only has a single entry for Windows 7; an autoloader (or something similar). I wasn't game to open that, since I think that was possibly what caused this mess in the first place. Is there any way to retrieve the other Windows 7 link? And can I omit those that I won't use commonly, or even just hide them away in a sub-menu?
Are there any other steps I need to follow to complete the GRUB setup itself?
Again, thanks. Between myself and a friend, nothing we found was successful in even coming close to fixing this! I cannot express my gratitude enough!

---

### Post by Quackers on 2010-12-26
I don't really know what happened to grub.
What those 2 commands did was to mount the Ubuntu 10.10 partition and then install grub to the mbr of sda again, but this time it knew where its boot files were.
We've not finished yet. One or two more things yet.
In a terminal copy/paste this please
```
sudo apt-get install gparted
```
That shoud install gparted. If no errors are reported please go to Applications > Administration > gparted.
When the screen opens it will scan any connected hard drives.
Once scanned it should report the partitions on drive sda.
Right-click on sda1 and choose "Manage flags" then in the window that pops up check the box marked "boot" and click close. Then click the green tick in the tool bar.
Once that is done close gparted (File > quit) and back in the terminal type
```
sudo update-grub
```
then watch the terminal screen as grub.cfg is configured. It should show a Windows Loader and an entry for Ubuntu 10.10 and an entry for Ubuntu 9.10.

If it does reboot and select the windows loader for sda1.
Beware! This may possibly boot the Windows recovery console (a black screen with a grey progress bar which turns white as "Windows files are loaded" - if it does don't panic. Just let it finish and when the blue/green recovery screen loads just reboot.
But, on the other hand it may boot into Windows 7 :-)
Please let us know.

---

### Post by mickliddy on 2010-12-26
I got an error every time I tried to install gparted through the terminal; but I found it in the Ubuntu Software Centre. That installed without any issues, and now GRUB has a link into Windows 7. It boots into Windows 7 without issue; though Windows then gives the option to boot normally or into recovery mode (I am not sure what this is all about; but this isn't the place to try and figure that out!).
Thanks for all of your help with this! :D
Is there any place I can go to find out how to get rid of GRUB entries that I don't use, or even hide them away in a submenu or something? And is there a Ubuntu for Dummies guide, or something like that?

---

### Post by wilee-nilee on 2010-12-26
Actually if the recovery mode for W7 actually works your lucky you never know if you will need it and wont know until you try it. The recovery will wipe the original W7 and install the original install at purchase hopefully not wiping the whole HD to do it.

The recovery can be removed at some point if you have a straight install dvd or verified images of W7 saved.

---

### Post by Quackers on 2010-12-26
If you are being offered the F8 screen in Windows, offering you a normal boot or other options, it may be that Windows thinks it needs a chkdsk running. This could be because the boot flag has been switched, or for some other reason.
I would boot into Windows and see below for details.

[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

For changing Grub menu entries, everything you need to know is here

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

or here

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

That's a pretty good result, well done :-)

---

### Post by mickliddy on 2010-12-26
Awesome, thanks guys. Have set a chkdsk to run when I reboot into Windows and am reading up about GRUB atm :D
Will figure out if I really want to change the menu of the bootloader later, when I understand it a bit more - I don't want it to break again! :S

---

### Post by Quackers on 2010-12-26
Good thinking :-)
BTW, if chkdsk runs and reports errors, you should re-run it until no errors are reported. Select the fix option when running chkdsk so that it finds and fixes bad sectors.

---

