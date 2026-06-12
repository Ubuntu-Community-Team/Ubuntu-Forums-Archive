---
title: "GRUB2 issues with Windows 7 partition"
date: 2011-02-06
forum: General Help
---

### Post by crimius on 2011-02-06
The full story:  I installed Windows 7 over some old linux partitions (just left them alone for a while), and everything was hunky dory for a while.  Earlier, I installed BackTrack4 R2 (why, would I install it instead of just use the LiveCD you ask?  It was 5 AM and I hadn't slept) and made some formatting changes.  I blew an old FAT partition away, as well as the remaining ext3 ones, and split half my space to be used between BT and Ubuntu.  I finished installing BT without a hitch on the first partition, and it boots and runs fine.  I installed Ubuntu onto the remaining freespace and merged the old FAT space (which was comparably small, only about 10 GB) to the end of the NTFS partition that Win7 was on.  Ubuntu finished installing fine, and boots fine.  GRUB didn't find my NTFS partition by itself, so I edited the 40_custom file and ran update-grub.  Windows now has a menu option, but all I get is a blank screen with a blinking white cursor.  I've seen one or two other forum posts with that description, but none had a solution.  After some digging, I found that instead of being listed as (hd0,5) as I expected in grub.cfg, they're listed in the (hd0,msdos5), and adjusted accordingly.  Output of boot_info script and current 40_custom file:

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 (on /dev/sda5)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos5)'
chainloader +1
}

```

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2010. But according to the info from fdisk, 
                       sda5 starts at sector 426270720.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *            187   488,389,860   488,389,674   5 Extended
/dev/sda5         426,270,720   488,389,860    62,119,141   7 HPFS/NTFS
/dev/sda6                 189   213,134,354   213,134,166  83 Linux
/dev/sda7         213,134,418   217,038,149     3,903,732  82 Linux swap / Solaris
/dev/sda8         217,038,848   426,268,671   209,229,824  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2: PTTYPE="dos" 
/dev/sda5        564E78244E77FAD7                       ntfs                                     
/dev/sda6        61084921-85bb-498e-a546-e56025832d49   ext3                                     
/dev/sda7        572aeceb-7ba5-48b8-aa09-fc9cd01e9e81   swap                                     
/dev/sda8        40f9557b-ad5c-48cb-836e-43aba203956d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
# kopt=root=UUID=61084921-85bb-498e-a546-e56025832d49 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=61084921-85bb-498e-a546-e56025832d49

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=61084921-85bb-498e-a546-e56025832d49/boot/grub/splash.xpm.gz

title		BackTrack 4 R2, kernel 2.6.35.8
uuid		61084921-85bb-498e-a546-e56025832d49
kernel		/boot/vmlinuz-2.6.35.8 root=UUID=61084921-85bb-498e-a546-e56025832d49 ro quiet splash 
initrd		/boot/initrd.img-2.6.35.8
quiet

title		BackTrack 4 R2, kernel 2.6.35.8 (recovery mode)
uuid		61084921-85bb-498e-a546-e56025832d49
kernel		/boot/vmlinuz-2.6.35.8 root=UUID=61084921-85bb-498e-a546-e56025832d49 ro  single
initrd		/boot/initrd.img-2.6.35.8

title		BackTrack 4 R2, memtest86+
uuid		61084921-85bb-498e-a546-e56025832d49
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=61084921-85bb-498e-a546-e56025832d49 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=572aeceb-7ba5-48b8-aa09-fc9cd01e9e81 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  43.1GB: boot/grub/menu.lst
  43.1GB: boot/grub/stage2
  43.1GB: boot/initrd.img-2.6.35.8
  43.2GB: boot/vmlinuz-2.6.35.8
  43.1GB: initrd.img
  43.2GB: vmlinuz

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
search --no-floppy --fs-uuid --set 40f9557b-ad5c-48cb-836e-43aba203956d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 40f9557b-ad5c-48cb-836e-43aba203956d
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
menuentry 'Ubuntu, with Linux 2.6.35-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 40f9557b-ad5c-48cb-836e-43aba203956d
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=40f9557b-ad5c-48cb-836e-43aba203956d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 40f9557b-ad5c-48cb-836e-43aba203956d
	echo	'Loading Linux 2.6.35-26-generic ...'
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=40f9557b-ad5c-48cb-836e-43aba203956d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 40f9557b-ad5c-48cb-836e-43aba203956d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=40f9557b-ad5c-48cb-836e-43aba203956d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 40f9557b-ad5c-48cb-836e-43aba203956d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=40f9557b-ad5c-48cb-836e-43aba203956d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 40f9557b-ad5c-48cb-836e-43aba203956d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 40f9557b-ad5c-48cb-836e-43aba203956d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 61084921-85bb-498e-a546-e56025832d49
	linux /boot/vmlinuz-2.6.35.8 root=UUID=61084921-85bb-498e-a546-e56025832d49 ro quiet splash
	initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 61084921-85bb-498e-a546-e56025832d49
	linux /boot/vmlinuz-2.6.35.8 root=UUID=61084921-85bb-498e-a546-e56025832d49 ro single
	initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, memtest86+ (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 61084921-85bb-498e-a546-e56025832d49
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 (on /dev/sda5)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos5)'
chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=40f9557b-ad5c-48cb-836e-43aba203956d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=572aeceb-7ba5-48b8-aa09-fc9cd01e9e81 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 158.5GB: boot/grub/core.img
 206.0GB: boot/grub/grub.cfg
 112.2GB: boot/initrd.img-2.6.35-22-generic
 112.2GB: boot/initrd.img-2.6.35-26-generic
 158.6GB: boot/vmlinuz-2.6.35-22-generic
 158.6GB: boot/vmlinuz-2.6.35-26-generic
 112.2GB: initrd.img
 112.2GB: initrd.img.old
 158.6GB: vmlinuz
 158.6GB: vmlinuz.old

```

I would appreciate any help :)

---

### Post by Krytarik on 2011-02-06
Hi crimius,

I'm a bit surprised that your disk doesn't has a primary partition at all, and a bit concerned about the following error message:
>     Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2010. But according to the info from fdisk, 
                       sda5 starts at sector 426270720.
Regarding the error, check the disk with Windows' own tools.

However, I had exact the same issue after moving Ubuntu and Windows to a new disk. Before that, Grub was able to boot Windows 7 as expected. Anything I tried was unsuccessful. But eventually downgrading to Grub legacy helped.

---

