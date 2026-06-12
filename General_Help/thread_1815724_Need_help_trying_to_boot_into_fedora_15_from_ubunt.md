---
title: "Need help trying to boot into fedora 15 from ubuntu 11.04"
date: 2011-07-31
forum: General Help
---

### Post by Ghostnik11 on 2011-07-31
Hi, I had recently installed fedora 15 along side my ubuntu 11.04 on my laptop.  At first I had problems with getting back into ubuntu after installing fedora 15 but found a solution which was to just use a live cd to reinstall my grub 2.  Now I am back in ubuntu 11.04 but can't get into fedora 15.  

Here is a look at my 40_custom:

```
menuentry "Fedora (2.6.38.6-26.rc1.fc15.i686)" {
set root=(hd0,2)
search --no-floppy --fs-uuid --set N2eBPJ-V1Kk-1jZH-A18h-WYEN-DTDh-qBUop3
kernel boot/vmlinuz-2.6.38.8-35.fc15.i686 root=UUID=N2eBPJ-V1Kk-1jZH-A18h-WYEN-DTDh-qBUop3 ro 		quiet splash
initrd boot/initramfs-2.6.38.8-35.fc15.i686.img
}

menuentry "Fedora (2.6.38.8-35.fc15.i686)" {
	root (hd0,2)
	kernel /vmlinuz-2.6.38.8-35.fc15.i686 ro root=/dev/mapper/vg_kingfedoralaptop-lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.8-35.fc15.i686.img
}

menuentry "Fedora" {
	insmod chain
	insmod ext2
	set root=(hd0,3)
	chainloader +1
}

menuentry "Fedora c" {
	insmod chain
	insmod ext2
	set root=(hd0,2)
	chainloader +1
}
```

I tried to chain load to my fedora 15 from grub 2 but when i get to grub boot option from restarting of computer i get errors saying: can't load.  Aslo when I try to as you see in the above example: lay a correct path for where my fedora 15 is and try to select that boot option, I get error, kernel has to be loaded first.

here is my fdisk:

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069510

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7833    62914560   83  Linux
/dev/sda2           11902       12162     2085889    5  Extended
/dev/sda3            7833        7897      512000   83  Linux
/dev/sda4            7897       11902    32171008   8e  Linux LVM
/dev/sda5           11902       12162     2085888   82  Linux swap / Solaris
```

Also here is my boot script into txt results:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97-71.fc15) is installed in the boot 
                       sector of sda1 and looks at sector 125860354 of the 
                       same hard drive for the stage2 file.  A stage2 file is 
                       at this location on /dev/sda.  Stage2 looks on 
                       partition #3 for /grub/grub.conf.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda4: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   125,831,167   125,829,120  83 Linux
/dev/sda2         191,199,230   195,371,007     4,171,778   5 Extended
/dev/sda5         191,199,232   195,371,007     4,171,776  82 Linux swap / Solaris
/dev/sda3         125,831,168   126,855,167     1,024,000  83 Linux
/dev/sda4         126,855,168   191,197,183    64,342,016  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ff980c21-18d1-4c7a-80e8-14637c1fe498   ext4       
/dev/sda3        533f25f8-b112-4066-aad0-800a558e69b1   ext4       
/dev/sda4        N2eBPJ-V1Kk-1jZH-A18h-WYEN-DTDh-qBUop3 LVM2_member 
/dev/sda5        4f7aec8c-5938-4fdf-ba13-720f9495b94c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/533f25f8-b112-4066-aad0-800a558e69b1 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4f7aec8c-5938-4fdf-ba13-720f9495b94c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  32.180702209 = 34.553765888   boot/grub/core.img                             1
  32.340839386 = 34.725711872   boot/grub/grub.cfg                             1
  15.397598267 = 16.533045248   boot/initrd.img-2.6.38-10-generic              2
  14.891994476 = 15.990157312   boot/initrd.img-2.6.38-8-generic               2
  15.196598053 = 16.317222912   boot/vmlinuz-2.6.38-10-generic                 2
  32.133281708 = 34.502848512   boot/vmlinuz-2.6.38-8-generic                  1
  15.397598267 = 16.533045248   initrd.img                                     2
  14.891994476 = 15.990157312   initrd.img.old                                 2
  15.196598053 = 16.317222912   vmlinuz                                        2
  32.133281708 = 34.502848512   vmlinuz.old                                    1

============================= sda3/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_kingfedoralaptop-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.8-35.fc15.i686)
	root (hd0,2)
	kernel /vmlinuz-2.6.38.8-35.fc15.i686 ro root=/dev/mapper/vg_kingfedoralaptop-lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.8-35.fc15.i686.img
 
title Fedora (2.6.38.6-26.rc1.fc15.i686)
	root (hd0,2)
	kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_kingfedoralaptop-lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
 
# added to try chainloading ubuntu
title ubuntu bootloader
set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
kernel /boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
chainloader +1

#added to try chainloading ubuntu
title ubuntu 11.04
	root (hd0,1)
	kernel	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
#	initrd	/boot/initrd.img-2.6.38-10-generic
#boot=/dev/sda1
	chainloader +1

title My Grub2 Ubuntu in (hd0,1)
root (hd0,1)
chainloader +1

title Ubuntu 11.04
root (hd0,1)
	kernel	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
chainloader +1

title Ubuntu 11.04
root (hd0,1)
kernel /boot/vmlinuz-2.6.38-10-generic root=/dev/sda1
initrd /boot/initrd.img-2.6.38-10-generic
chainloader +1

title Ubuntu 11.04
root (hd0,1)
kernel /boot/vmlinuz-2.6.38-10-generic root=/dev/sda,msdos1
initrd /boot/initrd.img-2.6.38-10-generic
chainloader +1

title Ubuntu 11.04
root (hd0,1)
kernel /boot/vmlinuz-2.6.38-10-generic root=/dev/sda,msdos1
initrd /boot/initrd.img-2.6.38-10-generic

title 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	root (hd0,1)
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	kernel	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic

title 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7 
	initrd	/boot/initrd.img-2.6.38-10-generic

title Ubuntu 11.04a
root (hd0,1)
kernel /grub/core.img
boot

title Ubuntu 11.04b
root (hd0,0)
kernel /grub/core.img
boot

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  60.041025162 = 64.468559872   grub/grub.conf                                 1
  60.041025162 = 64.468559872   grub/menu.lst                                  1
  60.015008926 = 64.440625152   grub/stage2                                    1
  60.031785011 = 64.458638336   initramfs-2.6.38.6-26.rc1.fc15.i686.img        2
  60.051093102 = 64.479370240   initramfs-2.6.38.8-35.fc15.i686.img            2
  60.012580872 = 64.438018048   vmlinuz-2.6.38.6-26.rc1.fc15.i686              1
  60.035815239 = 64.462965760   vmlinuz-2.6.38.8-35.fc15.i686                  1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  cc b5 ce 08 cc b5 ce 08  cc b5 ce 08 cc b5 ce 08  |................|
*
000001b0  cc b5 ce 08 cc b5 ce 08  cc b5 ce 08 cc b5 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 3f 00 00 00  |............?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

What am I doing wrong?  How can I get ubuntu's grub 2 to recognise my fedora 15 partition and allow me during grub boot options to select which one I please and boot?  Thanks in advance.

---

### Post by wojox on 2011-07-31
Once you install Grub2 from the Live-CD you should boot straight into Ubuntu, then run:

```
sudo update-grub
```

---

### Post by Ghostnik11 on 2011-07-31
> **wojox said:**
> Once you install Grub2 from the Live-CD you should boot straight into Ubuntu, then run:

```
sudo update-grub
```

Yep did that and grub 2 still doesn't see my fedora 15 partition and give me the option to boot into it.

---

### Post by oldfred on 2011-07-31
It looks like you installed fedora's grub legacy to the partition boot sector of Ubuntu. Since Ubuntu will not use it, I guess it is ok, but I would prefer it were in the Fedora boot partition.

You can chainboot to Fedora by specifing the Ubuntu partition (since that has old grub).

It looks like the chain entires you added were to menu.lst for Fedora's grub but you cannot get there since you are booting Ubuntu's grub2.

Add this to 40_custom:

gksudo gedit /etc/grub.d/40_custom
#then:
sudo update-grub

```
menuentry "Chainload Other Systems Grub Menu on sda1" {
set root=(hd0,1)
chainloader +1
}

```

Also:
HowTo: add Fedora 15 to Maverick Grub 2
[http://ubuntuforums.org/showthread.php?t=1714170](http://ubuntuforums.org/showthread.php?t=1714170)
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27 chainload
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)

---

### Post by Ghostnik11 on 2011-07-31
> **oldfred said:**
> It looks like you installed fedora's grub legacy to the partition boot sector of Ubuntu. Since Ubuntu will not use it, I guess it is ok, but I would prefer it were in the Fedora boot partition.

You can chainboot to Fedora by specifing the Ubuntu partition (since that has old grub).

It looks like the chain entires you added were to menu.lst for Fedora's grub but you cannot get there since you are booting Ubuntu's grub2.

Add this to 40_custom:

gksudo gedit /etc/grub.d/40_custom
#then:
sudo update-grub

```
menuentry "Chainload Other Systems Grub Menu on sda1" {
set root=(hd0,1)
chainloader +1
}

```

Also:
HowTo: add Fedora 15 to Maverick Grub 2
[http://ubuntuforums.org/showthread.php?t=1714170](http://ubuntuforums.org/showthread.php?t=1714170)
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27 chainload
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)

yes that did the trick.  I get boot into fedora 15 following your commands, thanks now that I am in fedora 15.  One more question over time will having my grub legacy on ubuntu partition cause problems?  If it will then I will change the fact that the grub legacy is on the ubuntu partition since i have access to fedora 15 again.  Thanks again for all those who helped me.

---

### Post by oldfred on 2011-07-31
Glad you got it working. :)

The only time it might cause an issue is if you delete the Ubuntu partition. But even if you did that you would plan ahead and reinstall the grub legacy to the MBR first.

You should not have to make any changes but if you want to.
I do not know equivalent commands in Fedora, as I know it does not use sudo.

In Ubuntu it woud be this to install grub to the partition boot sector from inside the install (not liveCD).
sudo grub-install /dev/sda3

Then you would have to update  the chain boot entry. 

I like to use the boot script to know what is installed where. Especially important for multiple installs and/or multiple drives. I have made it part of my standard rsync backup to have a current results.txt in every backup.

---

### Post by Ghostnik11 on 2011-08-01
> **oldfred said:**
> Glad you got it working. :)

The only time it might cause an issue is if you delete the Ubuntu partition. But even if you did that you would plan ahead and reinstall the grub legacy to the MBR first.

You should not have to make any changes but if you want to.
I do not know equivalent commands in Fedora, as I know it does not use sudo.

In Ubuntu it woud be this to install grub to the partition boot sector from inside the install (not liveCD).
sudo grub-install /dev/sda3

Then you would have to update  the chain boot entry. 

I like to use the boot script to know what is installed where. Especially important for multiple installs and/or multiple drives. I have made it part of my standard rsync backup to have a current results.txt in every backup.

Okay cool, ran the command in terminal after booting into fedora 15.  This is results: 
```

[root@king-fedora-laptop ~]# grub-install /dev/sda3
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

# this device map was generated by anaconda
(hd0)     /dev/sda
[root@king-fedora-laptop ~]# fdisk -l
```

So now my grub 1 is on my fedora 15 partition where its suppose to be instead of my ubuntu partition.  In terms of chain boot entry, will have to head back to ubuntu 11.04 and change it there as grub 2 controls MBR and will have to tell it that fedora grub is in /dev/sda3.

---

### Post by Ghostnik11 on 2011-08-01
> **Ghostnik11 said:**
> Okay cool, ran the command in terminal after booting into fedora 15.  This is results: 
```

[root@king-fedora-laptop ~]# grub-install /dev/sda3
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

# this device map was generated by anaconda
(hd0)     /dev/sda
[root@king-fedora-laptop ~]# fdisk -l
```

So now my grub 1 is on my fedora 15 partition where its suppose to be instead of my ubuntu partition.  In terms of chain boot entry, will have to head back to ubuntu 11.04 and change it there as grub 2 controls MBR and will have to tell it that fedora grub is in /dev/sda3.

thank you oldfred, as I have just changed the menu entry to: 

```
menuentry "Chainload Other Systems Grub Menu on sda1" {
set root=(hd0,3)
chainloader +1
}
```

It still boots into fedora when i bring up the grub boot options after a restart and when i select that entry it allows me to boot into fedora 15.  The one thing I don't get is how come grub 1 is still installed in my sda 1 section where ubuntu is, as you can see in this new boot script info i generated.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97-71.fc15) is installed in the boot 
                       sector of sda1 and looks at sector 125860354 of the 
                       same hard drive for the stage2 file.  A stage2 file is 
                       at this location on /dev/sda.  Stage2 looks on 
                       partition #3 for /grub/grub.conf.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97-71.fc15) is installed in the boot 
                       sector of sda3 and looks at sector 125859362 of the 
                       same hard drive for the stage2 file.  A stage2 file is 
                       at this location on /dev/sda.  Stage2 looks on 
                       partition #3 for /grub/grub.conf.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda4: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   125,831,167   125,829,120  83 Linux
/dev/sda2         191,199,230   195,371,007     4,171,778   5 Extended
/dev/sda5         191,199,232   195,371,007     4,171,776  82 Linux swap / Solaris
/dev/sda3         125,831,168   126,855,167     1,024,000  83 Linux
/dev/sda4         126,855,168   191,197,183    64,342,016  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ff980c21-18d1-4c7a-80e8-14637c1fe498   ext4       
/dev/sda3        533f25f8-b112-4066-aad0-800a558e69b1   ext4       
/dev/sda4        N2eBPJ-V1Kk-1jZH-A18h-WYEN-DTDh-qBUop3 LVM2_member 
/dev/sda5        4f7aec8c-5938-4fdf-ba13-720f9495b94c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

menuentry "Chainload Other Systems Grub Menu on sda1" {
set root=(hd0,3)
chainloader +1
}


### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4f7aec8c-5938-4fdf-ba13-720f9495b94c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  32.180702209 = 34.553765888   boot/grub/core.img                             1
  46.548110962 = 49.980653568   boot/grub/grub.cfg                             1
  15.397598267 = 16.533045248   boot/initrd.img-2.6.38-10-generic              2
  14.891994476 = 15.990157312   boot/initrd.img-2.6.38-8-generic               2
  15.196598053 = 16.317222912   boot/vmlinuz-2.6.38-10-generic                 2
  32.133281708 = 34.502848512   boot/vmlinuz-2.6.38-8-generic                  1
  15.397598267 = 16.533045248   initrd.img                                     2
  14.891994476 = 15.990157312   initrd.img.old                                 2
  15.196598053 = 16.317222912   vmlinuz                                        2
  32.133281708 = 34.502848512   vmlinuz.old                                    1

============================= sda3/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_kingfedoralaptop-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.8-35.fc15.i686)
	root (hd0,2)
	kernel /vmlinuz-2.6.38.8-35.fc15.i686 ro root=/dev/mapper/vg_kingfedoralaptop-lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.8-35.fc15.i686.img
 
title Fedora (2.6.38.6-26.rc1.fc15.i686)
	root (hd0,2)
	kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_kingfedoralaptop-lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_root rd_LVM_LV=vg_kingfedoralaptop/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
 
# added to try chainloading ubuntu
title ubuntu bootloader
set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
kernel /boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
chainloader +1

#added to try chainloading ubuntu
title ubuntu 11.04
	root (hd0,1)
	kernel	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
#	initrd	/boot/initrd.img-2.6.38-10-generic
#boot=/dev/sda1
	chainloader +1

title My Grub2 Ubuntu in (hd0,1)
root (hd0,1)
chainloader +1

title Ubuntu 11.04
root (hd0,1)
	kernel	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
chainloader +1

title Ubuntu 11.04
root (hd0,1)
kernel /boot/vmlinuz-2.6.38-10-generic root=/dev/sda1
initrd /boot/initrd.img-2.6.38-10-generic
chainloader +1

title Ubuntu 11.04
root (hd0,1)
kernel /boot/vmlinuz-2.6.38-10-generic root=/dev/sda,msdos1
initrd /boot/initrd.img-2.6.38-10-generic
chainloader +1

title Ubuntu 11.04
root (hd0,1)
kernel /boot/vmlinuz-2.6.38-10-generic root=/dev/sda,msdos1
initrd /boot/initrd.img-2.6.38-10-generic

title 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	root (hd0,1)
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root ff980c21-18d1-4c7a-80e8-14637c1fe498
	kernel	/boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic

title 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os
	root (hd0,1)
	kernel /boot/vmlinuz-2.6.38-10-generic root=UUID=ff980c21-18d1-4c7a-80e8-14637c1fe498 ro   quiet splash vt.handoff=7 
	initrd	/boot/initrd.img-2.6.38-10-generic

title Ubuntu 11.04a
root (hd0,1)
kernel /grub/core.img
boot

title Ubuntu 11.04b
root (hd0,0)
kernel /grub/core.img
boot

--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  60.040532112 = 64.468030464   grub/grub.conf                                 1
  60.040532112 = 64.468030464   grub/menu.lst                                  1
  60.014535904 = 64.440117248   grub/stage2                                    1
  60.031785011 = 64.458638336   initramfs-2.6.38.6-26.rc1.fc15.i686.img        2
  60.051093102 = 64.479370240   initramfs-2.6.38.8-35.fc15.i686.img            2
  60.012580872 = 64.438018048   vmlinuz-2.6.38.6-26.rc1.fc15.i686              1
  60.035815239 = 64.462965760   vmlinuz-2.6.38.8-35.fc15.i686                  1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  cc b5 ce 08 cc b5 ce 08  cc b5 ce 08 cc b5 ce 08  |................|
*
000001b0  cc b5 ce 08 cc b5 ce 08  cc b5 ce 08 cc b5 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 3f 00 00 00  |............?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

How can I get the /dev/sda1 to have ubuntu's grub2 and not fedora's grub  located there as fedora's grub is now on /dev/sda3?

---

### Post by oldfred on 2011-08-01
There is no easy way to erase a partition boot sector and reinstalling somewhere else does not remove it. Windows uses it (and Lilo) and as you have done you can install grub legacy to the partition boot sector, but you do not have to clear it. It just normally is not used by grub2. If grub legacy is in MBR it also did not use partition boot sector, it is only used when chainloading.

Having some data in the PBR will not cause an issue, so I would just leave it.

---

### Post by Ghostnik11 on 2011-08-01
> **oldfred said:**
> There is no easy way to erase a partition boot sector and reinstalling somewhere else does not remove it. Windows uses it (and Lilo) and as you have done you can install grub legacy to the partition boot sector, but you do not have to clear it. It just normally is not used by grub2. If grub legacy is in MBR it also did not use partition boot sector, it is only used when chainloading.

Having some data in the PBR will not cause an issue, so I would just leave it.

Okay, cool, thanks for help and solution to my problem.

---

