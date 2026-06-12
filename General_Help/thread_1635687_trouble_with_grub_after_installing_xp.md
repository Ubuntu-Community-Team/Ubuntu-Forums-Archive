---
title: "trouble with grub after installing xp"
date: 2010-12-02
forum: General Help
---

### Post by owners4life5 on 2010-12-02
hello,

last night i installed windows xp, and of course, it took over my grub menu..

a couple of days ago, i installed windows 7 onto a different computer, and it also took over, and i followed these instructions to fix it:
[http://ubuntuforums.org/showthread.php?t=1632439](http://ubuntuforums.org/showthread.php?t=1632439).
so last night, being that i was rather tired, i followed the problem-specific instructions, like a complete dope for the xp installation also.

now, the only o.s. it shows is maverick in my grub menu, and everything that is actually installed is maverick, lucid, and xp.

i downloaded and ran the script like the fellow in the last problem told me to do, and here is the output of that:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1             192,780    42,762,239    42,569,460  83 Linux
/dev/sda2    *     42,762,240    81,242,111    38,479,872   7 HPFS/NTFS
/dev/sda3          81,242,112    88,080,383     6,838,272  83 Linux
/dev/sda4         115,507,198   156,301,311    40,794,114   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5         115,507,200   132,362,239    16,855,040  83 Linux
/dev/sda6         151,836,672   153,501,695     1,665,024  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        41397e85-327f-4e99-a097-73c1047aa8f4   ext4                                     
/dev/sda2        0C909397909385BC                       ntfs                                     
/dev/sda3        87e76d77-53a6-4b00-a75a-78f6ababa007   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        fefcd091-0a5c-420c-95e9-fea2163af41d   ext4                                     
/dev/sda6        886dddc5-3585-4986-a49e-60a29e091369   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=41397e85-327f-4e99-a097-73c1047aa8f4

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.32-25-generic
uuid		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
uuid		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.10, kernel 2.6.32-24-generic
uuid		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-24-generic (recovery mode)
uuid		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Chainload into GRUB 2
root		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		41397e85-327f-4e99-a097-73c1047aa8f4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=20a48cc7-29e2-44c6-8883-ebcfbb38a481 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   1.4GB: boot/grub/core.img
  10.7GB: boot/grub/grub.cfg
  13.7GB: boot/grub/menu.lst
  13.7GB: boot/grub/stage2
   1.6GB: boot/initrd.img-2.6.32-24-generic
   1.5GB: boot/initrd.img-2.6.32-25-generic
   3.4GB: boot/initrd.img-2.6.35-22-generic
  12.4GB: boot/initrd.img-2.6.35-23-generic
   1.5GB: boot/vmlinuz-2.6.32-24-generic
   1.5GB: boot/vmlinuz-2.6.32-25-generic
   1.6GB: boot/vmlinuz-2.6.35-22-generic
   3.9GB: boot/vmlinuz-2.6.35-23-generic
  12.4GB: initrd.img
   3.4GB: initrd.img.old
   3.9GB: vmlinuz
   1.6GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=fefcd091-0a5c-420c-95e9-fea2163af41d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=fefcd091-0a5c-420c-95e9-fea2163af41d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=fefcd091-0a5c-420c-95e9-fea2163af41d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=fefcd091-0a5c-420c-95e9-fea2163af41d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=fefcd091-0a5c-420c-95e9-fea2163af41d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=fefcd091-0a5c-420c-95e9-fea2163af41d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fefcd091-0a5c-420c-95e9-fea2163af41d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10, kernel 2.6.35-23-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-22-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.32-25-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.32-24-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.32-24-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=41397e85-327f-4e99-a097-73c1047aa8f4 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Chainload into GRUB 2 (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/grub/core.img 
}
menuentry "Ubuntu 10.10, memtest86+ (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 41397e85-327f-4e99-a097-73c1047aa8f4
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=fefcd091-0a5c-420c-95e9-fea2163af41d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=886dddc5-3585-4986-a49e-60a29e091369 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  62.2GB: boot/grub/core.img
  61.4GB: boot/grub/grub.cfg
  59.6GB: boot/initrd.img-2.6.32-21-generic
  62.1GB: boot/initrd.img-2.6.32-25-generic
  61.9GB: boot/initrd.img-2.6.32-26-generic
  62.2GB: boot/vmlinuz-2.6.32-21-generic
  62.2GB: boot/vmlinuz-2.6.32-25-generic
  62.2GB: boot/vmlinuz-2.6.32-26-generic
  61.9GB: initrd.img
  62.1GB: initrd.img.old
  62.2GB: vmlinuz
  62.2GB: vmlinuz.old
```

any help is greatly appreciated,

---

### Post by wilee-nilee on 2010-12-02
**Grub 0.97** is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub**/menu.lst** /boot/grub/**grub.cfg** /etc/fstab 
                       /boot/grub/core.img


So this is quite the conundrum, you have grub-legacy highlighted in the MBR and in 10.10 with grub2, but in the 10.04 install it just shows grub2. The script though shows grub-legacy and grub2 file listings so I would hold on for a little help here. I think I know the fix but I may be incorrect better to error on the safe side here.

Looks like you used a live cd to load the mbr that was to old and ended up with the grub-legacy. Fixable just wait for help.

---

### Post by owners4life5 on 2010-12-02
okay...thanks for the advice.
*bump*

---

### Post by wilee-nilee on 2010-12-02
> **owners4life5 said:**
> okay...thanks for the advice.
*bump* Sporadically there are knowledgeable users on this late in the US but the daytime is when the regulars who can line you up are on so if you need some sleep I would do it.;)

---

### Post by owners4life5 on 2010-12-02
don.t worry, i.m just waking up, not falling asleep :)

i have school, early to bed, early to rise.

---

### Post by oldfred on 2010-12-02
It would be best to cleanly uninstall both grub & grub2 and reinstall grub2.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

You have two systems, so which ever one you mount will be the default that grub boots. A sudo update-grub will make sure you have both in the grub menu.

You have another partition issue.
> Extended  partition  linking to another extended partitionBut I do not see the exact issue. Someone else may.
Testdisk may be the easiest way to fix it, but I am not sure. Since it looks correct it just may need the partition table rewritten or updated.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Once you boot windows you may want to update boot.ini as it still refers to another copy of windows in sda3.
How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

---

