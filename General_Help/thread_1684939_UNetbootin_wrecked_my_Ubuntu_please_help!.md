---
title: "UNetbootin wrecked my Ubuntu please help!"
date: 2011-02-09
forum: General Help
---

### Post by ayoubson on 2011-02-09
I would be grateful if you can help me, yesterday I tried out the new UNetbootin ISO boot feature as mentioned on Webupd8 ([click here to see]("http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html")). I have Ubuntu 10.10 (32-bit) installed on my desktop, I installed UNetbootin and then used it to try out a Linux Mint 10 ISO I had, with the goal of it booting from Grub2 menu. I had the Mint ISO on my Ubuntu desktop and I used UNetbootin to locate it and setup the Grub2 boot option as mentioned.

I then rebooted as instructed and I booted Linux Mint via the UNetbootin feature and it worked really well. Afterwards I restarted my computer and tried to boot to my regular Ubuntu OS, all I got was a blank screen than a screen with Ubuntu 10.10 written on it and it just hung there for a long time with no further progress (I tried to leave there for a very long time).

I tried to boot several times and through all the kernels I had on my Grub menu with the same results. I used a live disk to check the file systems of my Ubuntu OS and every thing seems to be there and thankfully non of my data has been deleted.

Can anyone help me sort out this mess? I would like to go back to my regular setup instead of reinstalling everything as I really worked hard on tweaking my system. Thank you.

---

### Post by wilee-nilee on 2011-02-09
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give a layout of what is where including the grub info needed.

---

### Post by ayoubson on 2011-02-09
Thanks @wilee-nilee. I have done what you advised. Please find the  results below. Please also excuse my messy system! The kernel I use  is "**Ubuntu, with Linux 2.6.35-25-generic-pae**". You can also find the  UNetbootin entry there as well.

```
                              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 1184845544 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   559,254,779   559,254,717   7 HPFS/NTFS
/dev/sda2         559,255,552 1,099,566,793   540,311,242   7 HPFS/NTFS
/dev/sda3       1,099,567,102 1,435,439,879   335,872,778   5 Extended
/dev/sda5       1,158,093,783 1,159,137,944     1,044,162  82 Linux swap / Solaris
/dev/sda6       1,159,138,008 1,210,337,099    51,199,092  83 Linux
/dev/sda7       1,210,337,163 1,435,439,879   225,102,717  83 Linux
/dev/sda8       1,099,567,104 1,155,586,047    56,018,944  83 Linux
/dev/sda9       1,155,588,096 1,158,092,799     2,504,704  82 Linux swap / Solaris
/dev/sda4       1,435,439,880 1,465,144,064    29,704,185   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        50BE9F14BE9EF1A8                       ntfs                                     
/dev/sda2        120D947C274F2B8B                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda5        e9e0d88d-ae65-4c0a-bc3a-bc428d973433   swap                                     
/dev/sda6        b6954ba2-33d4-42c8-9732-8666e3fe4213   ext4                                     
/dev/sda7        f17d1ac2-865a-43be-ac9e-9bd7f87a6bd4   ext4                                     
/dev/sda8        401d3b2d-7c7f-48e0-b00c-990d97c18f76   ext4                                     
/dev/sda9        40d4e001-08b4-4e0b-837d-0c1a3d69a597   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set b6954ba2-33d4-42c8-9732-8666e3fe4213
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set b6954ba2-33d4-42c8-9732-8666e3fe4213
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b6954ba2-33d4-42c8-9732-8666e3fe4213
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6954ba2-33d4-42c8-9732-8666e3fe4213 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b6954ba2-33d4-42c8-9732-8666e3fe4213
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b6954ba2-33d4-42c8-9732-8666e3fe4213 ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b6954ba2-33d4-42c8-9732-8666e3fe4213
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b6954ba2-33d4-42c8-9732-8666e3fe4213
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 50be9f14be9ef1a8
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=b6954ba2-33d4-42c8-9732-8666e3fe4213 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=f17d1ac2-865a-43be-ac9e-9bd7f87a6bd4 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=e9e0d88d-ae65-4c0a-bc3a-bc428d973433 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 606.6GB: boot/grub/core.img
 595.9GB: boot/grub/grub.cfg
 593.9GB: boot/initrd.img-2.6.35-22-generic
 606.6GB: boot/vmlinuz-2.6.35-22-generic
 593.9GB: initrd.img
 606.6GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set default="2"
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
search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.37-020637-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    linux    /boot/vmlinuz-2.6.37-020637-generic root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.37-020637-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-020637-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    echo    'Loading Linux 2.6.37-020637-generic ...'
    linux    /boot/vmlinuz-2.6.37-020637-generic root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.37-020637-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 401d3b2d-7c7f-48e0-b00c-990d97c18f76
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 50be9f14be9ef1a8
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b6954ba2-33d4-42c8-9732-8666e3fe4213
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=b6954ba2-33d4-42c8-9732-8666e3fe4213 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b6954ba2-33d4-42c8-9732-8666e3fe4213
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=b6954ba2-33d4-42c8-9732-8666e3fe4213 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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


menuentry "UNetbootin" {
    set root=(hd0,8)
    linux  /boot/ubnkern file=/cdrom/preseed/mint.seed boot=casper quiet splash --
    initrd /boot/ubninit 
}

menuentry "Start Linux Mint" {
    set root=(hd0,7)
    linux /casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper  quiet splash --
    initrd /casper/initrd.lz
}

menuentry "Start Linux Mint (compatibility mode)" {
    set root=(hd0,7)
    linux /casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper xforcevesa  ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
    initrd /casper/initrd.lz
}

menuentry "Check the integrity of the DVD" {
    set root=(hd0,7)
    linux /casper/vmlinuz boot=casper integrity-check  quiet splash --
    initrd /casper/initrd.lz
}

menuentry "Memory Test" {
    set root=(hd0,7)
    linux /isolinux/memtest 
    initrd /boot/ubninit
}

menuentry "Boot from local drive" {
    set root=(hd0,7)
    linux /boot/ubnkern 
    initrd /boot/ubninit
}


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=40d4e001-08b4-4e0b-837d-0c1a3d69a597 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 565.2GB: boot/grub/core.img
 586.5GB: boot/grub/grub.cfg
 570.3GB: boot/initrd.img-2.6.35-22-generic-pae
 568.7GB: boot/initrd.img-2.6.35-23-generic-pae
 569.1GB: boot/initrd.img-2.6.35-24-generic-pae
 591.1GB: boot/initrd.img-2.6.35-25-generic-pae
 577.7GB: boot/initrd.img-2.6.37-020637-generic
 565.2GB: boot/vmlinuz-2.6.35-22-generic-pae
 569.4GB: boot/vmlinuz-2.6.35-23-generic-pae
 568.1GB: boot/vmlinuz-2.6.35-24-generic-pae
 575.9GB: boot/vmlinuz-2.6.35-25-generic-pae
 566.4GB: boot/vmlinuz-2.6.37-020637-generic
 591.1GB: initrd.img
 577.7GB: initrd.img.old
 575.9GB: vmlinuz
 566.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde  
```

---

### Post by wilee-nilee on 2011-02-09
With a quick look it looks as though the mbr wants to boot from sda8, the script shows it being sda6 before I believe.

What you should have besides a Ubuntu cd is a supergrub2 disk if your going to mess around like this.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Here is a link for reloading grub2, it opens at the reload from a live cd.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

Since it looks like sda6 is there I would reload it first, to see if your back in.

---

### Post by ayoubson on 2011-02-10
Thank you very much for your advice thus far, I think we are heading in the right direction. I think the old grub/boot was in sda8, not very sure now.  
I also think I exacerbated the problem! I tried to follow some advice from elsewhere from previous posts, and now when i boot there is no Grub menu at all, just a screen with a flashing cursor.

Can anyone provide more specific help based on the above updated Boot Info Script?

---

### Post by wilee-nilee on 2011-02-10
So the link gives you these two commands run them from the terminal on the booted Ubuntu live cd/thumb, assuming the partitions are the same.

```
sudo mount /dev/sda6 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot to  the install and refresh the GRUB 2 menu with sudo update-grub

If sda8 is correct the first command would just have the number change to sda8 the second command remains sda.

---

### Post by ayoubson on 2011-02-10
Thanks. 

After running the second code:
sudo grub-install --root-directory=/mnt /dev/sda
I get the following message: grub-probe: **error: cannot find a device for /boot (is /dev mounted?).**

---

### Post by wilee-nilee on 2011-02-10
If it was me I would use the supergrub2 disk I have laying around to boot into Ubuntu and install grub from there to the mbr.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

If this gets you in just run from a terminal.
sudo grub-install /dev/sda
then 
sudo update-grub.

---

### Post by amsterdamharu on 2011-02-10
Looks like grub files are on sda8, you don't have a seporate boot partition:

fstab:[FONT=monospace]
[/FONT]UUID=401d3b2d-7c7f-48e0-b00c-990d97c18f76 /               ext4    errors=remount-ro 0       1
blkid:[FONT=monospace]
[/FONT]/dev/sda8        401d3b2d-7c7f-48e0-b00c-990d97c18f76   ext4 


That's why it can't find core.img on sda6. I think you install grub on sda8:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda8 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by sarge77 on 2011-05-01
Ok I have same problems but my ubuntu is on sdb1 and my so my command would be this hopefully

 	Code:
 	sudo mount /dev/sdb1 /mnt 
then
 	Code:
 	sudo grub-install --root-directory=/mnt /dev/sda 
would this be right because tutorial says install grub to root directory and install grub to mounted partition

---

### Post by sarge77 on 2011-05-01
Ok I have same problems but my ubuntu is on sdb1 and my so my command would be this hopefully

 
   > sudo mount /dev/sdb1 /mnt 

then

     
   >   sudo grub-install --root-directory=/mnt /dev/sda 

would this be right because tutorial says install grub to root directory and install grub to mounted partition

---

### Post by sarge77 on 2011-05-01
my error say:
 
target filesystem doesnt have requested /sbin/init.
No init found. Try passing init= bootarg.


Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built in shell (ash)
Enter 'help' for list of built in commands

(initramfs) _

Doesnt matter how many times I do grub update i still get this I might just have to use another linux distro to savage my home folder and reinstall hopefully i find another outcome that works better thanks

I just read on this forum to use gparted check disk to solve problem

---

### Post by sarge77 on 2011-05-01
check disc doesnt work just going to copy home directory maybe upgrade to 11.04 see what happens

not going to use unetbooting again it did this 2 times even in windows virtualbox is safer

---

