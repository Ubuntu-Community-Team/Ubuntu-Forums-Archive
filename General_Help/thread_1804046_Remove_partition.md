---
title: "Remove partition"
date: 2011-07-14
forum: General Help
---

### Post by andlinux on 2011-07-14
I've got the following problem.

I have a 250 GB hard disk in my laptop, Ubuntu is installed on this one and I always updated to a new version. Since that 11.04 came out, I made another partition and did a fresh installation of 11.04 on this partition.

Now I have this old partition and I want to get rid of it so I have extra free space.

The problem is that this partition has a boot option and I'm not sure if I can remove it, maybe my system won't start if I remove it ?
As you can see on the picture, the old partition is a lot bigger.
There are also the swap partitions, 1 of them can be removed.


See the image.

---

### Post by Lazaruss on 2011-07-14
Specifically, which partition do you want to remove, and which partition contains the bootloader?

---

### Post by andlinux on 2011-07-15
I want to remove /dev/sda1 and as you can see that has a boot option.

---

### Post by dasan on 2011-07-15
I hope you can remove the partition without much issue..
only thing is you will lose the boot loader and correcting grub will solve that for you..

It is always recommended that when you want to upgrade always you better keep your root and home as separate drive which will help to remove all root and put new things easily

---

### Post by coffeecat on 2011-07-15
> **andlinux said:**
> I want to remove /dev/sda1 and as you can see that has a boot option.

You can ignore the boot flag. The boot flag is only needed by Windows and is irrelevant to Linux.

Your current Ubuntu root partition is sda7, and sda1 appears to be unmounted so simply reformatting it or even simply deleting everything on it will give you an empty usable partition, but before doing that it would be best to check the output of the boot script (see below). Choosing which swap partition to delete is a little more tricky in that both are in use. The best thing would be to run the boot info script which will give us an overview of your system. Go to:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there and post the contents of your RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity.

How do you want to use the space currently occupied by the 162GiB sda1 partition? It's a primary partition, whereas all your other partitions are logical ones, which will add a slight complication if you wish to merge the space with one of the other partitions.

---

### Post by andlinux on 2011-07-16
Sorry for the late reply but here is the result of the txt file.

```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Schijf /dev/sda: 250.1 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders, totaal 488397168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   340,439,940   340,439,878  83 Linux
/dev/sda2         340,441,086   488,392,064   147,950,979   5 Extended
/dev/sda5         468,519,723   488,392,064    19,872,342  82 Linux swap / Solaris
/dev/sda6         463,204,352   468,518,911     5,314,560  82 Linux swap / Solaris
/dev/sda7         340,441,088   463,202,303   122,761,216  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        878a6980-26c3-4c54-801f-a06cd4265c47   ext4       
/dev/sda5        7b4dbe51-03ca-418c-ad24-443d660754f1   swap       
/dev/sda6        f4e6e0e5-ebb1-43b5-9c8e-d777d7faa0f9   swap       
/dev/sda7        dbdce3c5-692e-4636-9a5d-57de0bb2fa82   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# kopt=root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=878a6980-26c3-4c54-801f-a06cd4265c47

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

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		878a6980-26c3-4c54-801f-a06cd4265c47
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic
quiet

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		878a6980-26c3-4c54-801f-a06cd4265c47
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.35-29-generic
uuid		878a6980-26c3-4c54-801f-a06cd4265c47
kernel		/boot/vmlinuz-2.6.35-29-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-29-generic
quiet

title		Ubuntu 11.04, kernel 2.6.35-29-generic (recovery mode)
uuid		878a6980-26c3-4c54-801f-a06cd4265c47
kernel		/boot/vmlinuz-2.6.35-29-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro  single
initrd		/boot/initrd.img-2.6.35-29-generic

title		Ubuntu 11.04, kernel 2.6.32-25-generic
uuid		878a6980-26c3-4c54-801f-a06cd4265c47
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 11.04, kernel 2.6.32-25-generic (recovery mode)
uuid		878a6980-26c3-4c54-801f-a06cd4265c47
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 11.04, kernel 2.6.28-17-generic
uuid		878a6980-26c3-4c54-801f-a06cd4265c47
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 11.04, kernel 2.6.28-17-generic (recovery mode)
uuid		878a6980-26c3-4c54-801f-a06cd4265c47
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 11.04, memtest86+
uuid		878a6980-26c3-4c54-801f-a06cd4265c47
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=878a6980-26c3-4c54-801f-a06cd4265c47 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7b4dbe51-03ca-418c-ad24-443d660754f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.698222637 = 0.749710848    boot/grub/menu.lst                             1
   2.242209911 = 2.407554560    boot/grub/stage2                               1
   5.249000072 = 5.636070912    boot/initrd.img-2.6.28-17-generic              2
  46.767051220 = 50.215738880   boot/initrd.img-2.6.32-25-generic              2
  39.941462994 = 42.886819328   boot/initrd.img-2.6.35-29-generic              2
 111.034335613 = 119.222210048  boot/initrd.img-2.6.38-8-generic               3
   5.024787426 = 5.395324416    boot/vmlinuz-2.6.28-17-generic                 1
 107.173724651 = 115.076910592  boot/vmlinuz-2.6.32-25-generic                 2
  28.871268749 = 31.000288768   boot/vmlinuz-2.6.35-29-generic                 1
  51.496432781 = 55.293873664   boot/vmlinuz-2.6.38-8-generic                  2
 111.034335613 = 119.222210048  initrd.img                                     3
  39.941462994 = 42.886819328   initrd.img.old                                 2
  51.496432781 = 55.293873664   vmlinuz                                        2
  28.871268749 = 31.000288768   vmlinuz.old                                    1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
set locale_dir=($root)/boot/grub/locale
set lang=nl_BE
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=1
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
menuentry 'Ubuntu, met Linux 2.6.39-0-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	linux	/boot/vmlinuz-2.6.39-0-generic root=UUID=dbdce3c5-692e-4636-9a5d-57de0bb2fa82 ro  vga=771  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.39-0-generic
}
menuentry 'Ubuntu, met Linux 2.6.39-0-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	echo	'Loading Linux 2.6.39-0-generic ...'
	linux	/boot/vmlinuz-2.6.39-0-generic root=UUID=dbdce3c5-692e-4636-9a5d-57de0bb2fa82 ro single  vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-0-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, met Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=dbdce3c5-692e-4636-9a5d-57de0bb2fa82 ro  vga=771  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, met Linux 2.6.38-8-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=dbdce3c5-692e-4636-9a5d-57de0bb2fa82 ro single  vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, met Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=dbdce3c5-692e-4636-9a5d-57de0bb2fa82 ro  vga=771  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, met Linux 2.6.35-28-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=dbdce3c5-692e-4636-9a5d-57de0bb2fa82 ro single  vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=dbdce3c5-692e-4636-9a5d-57de0bb2fa82 ro  vga=771  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-31-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=dbdce3c5-692e-4636-9a5d-57de0bb2fa82 ro single  vga=771
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root dbdce3c5-692e-4636-9a5d-57de0bb2fa82
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 11.04, kernel 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 878a6980-26c3-4c54-801f-a06cd4265c47
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro quiet splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 878a6980-26c3-4c54-801f-a06cd4265c47
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu 11.04, kernel 2.6.35-29-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 878a6980-26c3-4c54-801f-a06cd4265c47
	linux /boot/vmlinuz-2.6.35-29-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro quiet splash
	initrd /boot/initrd.img-2.6.35-29-generic
}
menuentry "Ubuntu 11.04, kernel 2.6.35-29-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 878a6980-26c3-4c54-801f-a06cd4265c47
	linux /boot/vmlinuz-2.6.35-29-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro single
	initrd /boot/initrd.img-2.6.35-29-generic
}
menuentry "Ubuntu 11.04, kernel 2.6.32-25-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 878a6980-26c3-4c54-801f-a06cd4265c47
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu 11.04, kernel 2.6.32-25-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 878a6980-26c3-4c54-801f-a06cd4265c47
	linux /boot/vmlinuz-2.6.32-25-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro single
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu 11.04, kernel 2.6.28-17-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 878a6980-26c3-4c54-801f-a06cd4265c47
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro quiet splash
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 11.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 878a6980-26c3-4c54-801f-a06cd4265c47
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=878a6980-26c3-4c54-801f-a06cd4265c47 ro single
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 11.04, memtest86+ (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 878a6980-26c3-4c54-801f-a06cd4265c47
	linux /boot/memtest86+.bin 
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
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=dbdce3c5-692e-4636-9a5d-57de0bb2fa82 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7b4dbe51-03ca-418c-ad24-443d660754f1 none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=f4e6e0e5-ebb1-43b5-9c8e-d777d7faa0f9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 202.474174500 = 217.404989440  boot/grub/core.img                             1
 192.644153595 = 206.850084864  boot/grub/grub.cfg                             1
 178.780273438 = 191.963856896  boot/initrd.img-2.6.32-31-generic              2
 178.223415375 = 191.365935104  boot/initrd.img-2.6.35-28-generic              2
 178.655273438 = 191.829639168  boot/initrd.img-2.6.38-8-generic               2
 196.964580536 = 211.489107968  boot/initrd.img-2.6.39-0-generic               2
 202.588741302 = 217.528004608  boot/vmlinuz-2.6.32-31-generic                 1
 178.327148438 = 191.477317632  boot/vmlinuz-2.6.35-28-generic                 2
 188.971988678 = 202.907127808  boot/vmlinuz-2.6.38-8-generic                  1
 215.600585938 = 231.499366400  boot/vmlinuz-2.6.39-0-generic                  2
 196.964580536 = 211.489107968  initrd.img                                     2
 178.655273438 = 191.829639168  initrd.img.old                                 2
 215.600585938 = 231.499366400  vmlinuz                                        2
 188.971988678 = 202.907127808  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  1d b0 e2 34 0e 14 7a 41  50 65 14 38 be d2 b0 84  |...4..zAPe.8....|
00000010  51 81 cc f2 29 65 27 63  61 72 74 65 60 ac c0 18  |Q...)e'carte`...|
00000020  d2 6c 67 7a ba c6 63 36  bd b3 ba 6d b1 3b e6 8f  |.lgz..c6...m.;..|
00000030  57 3e 63 f6 72 0d 75 8e  ee 2a 39 c4 8f 29 65 27  |W>c.r.u..*9..)e'|
00000040  63 61 72 74 65 6c 03 a0  03 63 55 80 02 a1 f5 2a  |cartel...cU....*|
00000050  72 35 b1 6e 54 de a5 a1  e6 ea c0 98 1e fe 55 8d  |r5.nT.........U.|
00000060  ea c4 7f 8e 14 67 2b 65  27 63 61 72 74 65 6c 65  |.....g+e'cartele|
00000070  27 40 a4 e3 2e 90 d4 19  f2 82 06 45 06 63 e3 bb  |'@.........E.c..|
00000080  72 c2 99 ae ed 19 dd fe  56 2f 3a b3 ab fa 77 f1  |r.......V/:...w.|
00000090  cc 2b 65 27 63 61 72 74  65 6c 65 72 19 a5 46 a3  |.+e'carteler..F.|
000000a0  c4 d6 aa d2 76 03 4b d1  3a 1f 31 34 74 96 e5 72  |....v.K.:.14t..r|
000000b0  cf 44 c2 21 c3 0c 96 aa  3f 57 76 86 29 65 27 63  |.D.!....?Wv.)e'c|
000000c0  61 72 74 65 6d ba 19 08  b6 fe 15 14 cf a3 2c e8  |artem.........,.|
000000d0  f0 06 01 83 2c a0 01 6e  50 09 91 b5 ca 1c 9b 72  |....,..nP......r|
000000e0  1c 83 61 f1 57 29 65 27  63 61 72 74 65 6e 06 a9  |..a.W)e'carten..|
000000f0  87 ef 5e bf 94 77 4d ee  63 f9 58 64 e3 ec 51 f7  |..^..wM.c.Xd..Q.|
00000100  9a 3c ee 36 86 13 94 fe  eb af 01 45 84 41 2a 65  |.<.6.......E.A*e|
00000110  27 63 61 72 74 65 6e 74  8d 2b 76 d2 02 1c fa f8  |'cartent.+v.....|
00000120  a2 87 ed af 0b 17 a2 8d  49 d1 ca dd 43 61 b2 4e  |........I...Ca.N|
00000130  e1 e2 aa 01 7e 0d 26 8f  29 65 27 63 61 72 74 65  |....~.&.)e'carte|
00000140  72 0f e3 63 73 0e d4 6f  4b 31 02 24 6f aa 8f 14  |r..cs..oK1.$o...|
00000150  1c 0e e1 d0 d2 23 02 24  d2 dd 9a 0b 1c b5 80 a1  |.....#.$........|
00000160  48 2a 65 27 63 61 72 74  65 72 61 bf f3 1b 6b bb  |H*e'cartera...k.|
00000170  08 1c 6a 0d 35 6a f3 44  46 96 b0 9c f8 c5 24 a5  |..j.5j.DF.....$.|
00000180  c2 b4 49 e2 ff 49 f4 66  b6 23 1c 2b 65 27 63 61  |..I..I.f.#.+e'ca|
00000190  72 74 65 72 61 69 38 3c  b6 cd a0 42 7e d8 1b 3c  |rterai8<...B~..<|
000001a0  3e c8 ed b1 12 0e 60 b7  3c f2 8a ef cd b7 b6 91  |>.....`.<.......|
000001b0  96 06 91 4c 70 b7 2b 65  27 63 61 72 74 65 00 fe  |...Lp.+e'carte..|
000001c0  ff ff 82 fe ff ff 2d 53  a2 07 56 3a 2f 01 00 fe  |......-S..V:/...|
000001d0  ff ff 05 fe ff ff 02 30  51 07 00 20 51 00 00 00  |.......0Q.. Q...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

Like you said I want to merge that free space of sda1 with sda7.

---

### Post by coffeecat on 2011-07-17
> **andlinux said:**
> 
Like you said I want to merge that free space of sda1 with sda7.

You can certainly delete sda1 or reformat it, but you can't "merge" it directly with sda7. What you would have to do is to delete sda1 completely, then enlarge the extended partition (sda2) backwards to include the space previously occupied by sda1, and then enlarge your logical sda7 partition which is inside the extended partition. It is fortunate that your three logical partitions are not in number order and that sda7 is at the beginning of the extended partition, otherwise you would not be able to do this.

You won't be able to do this from within your permanent installation. You will have to use an Ubuntu live CD or USB for this. When you open Gparted in the live session, you will find that both swap partitions (sda5 and sda6) will be enabled. Right-click on each in turn and choose "swapoff". Only then will you see the padlock icon disappear from sda2, making it resizable.

A few other points:

By the way, both your swap partitions are referenced in your sda7 /etc/fstab. If you wish to delete one of the swap partitions, you'll need to edit /etc/fstab.

IMPORTANT - backup all your data before doing this. Resizing partitions always runs the risk of something going wrong. Be warned that resizing sda7 to the left by 160+GiB will take a long time - perhaps 2-3 hours.

If you do this you will end up with a system with no primary partitions - only logicals inside an extended. This is not a problem - just unusual.

FINALLY - once you've enlarged sda7 and booted into Ubuntu again, open a terminal and run:

```
sudo update-grub
```

This will get rid of the superfluous sda1 menu entries.

---

### Post by andlinux on 2011-07-18
Well I started it, I booted from gparted-live and did the things you said. But it will take some time.

But I didn't do anything with the swap partitions, I can do what I want with them I don't see a lock. That's why I leave them.

---

### Post by andlinux on 2011-07-18
All operations successful. After gparted-live finished I did a reboot and it loaded ubuntu without a problem. Then I did update-grub.

Big thanks :)

---

### Post by dasan on 2011-07-20
Please mark as solved
Thread tools - Mark Thread as Solved

---

