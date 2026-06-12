---
title: "Won't boot after moving to new hard drive and partition structure"
date: 2010-12-09
forum: General Help
---

### Post by Tanath on 2010-12-09
**Background:**

Old drive is dying, so I copied the system over to my new drive. I've moved /home and /tmp to separate partitions and updated fstab and grub with the appropriate UUIDs from blkid. Grub wasn't loading but that's been fixed now.

**Problem:**

The problem now is that when I boot I get the following screen:

[FONT="Courier New"]Errors were found while checking the disk drive for /

Press F to attempt to fix the errors, I to ignore, S to skip mounting or M for manual recovery[/FONT]

F doesn't work, and in manual recovery the file system is read-only. How to proceed?

---

### Post by wilee-nilee on 2010-12-09
> **Tanath said:**
> **Background:**

Old drive is dying, so I copied the system over to my new drive. I've moved /home and /tmp to separate partitions and updated fstab and grub with the appropriate UUIDs from blkid. Grub wasn't loading but that's been fixed now.

**Problem:**

The problem now is that when I boot I get the following screen:

[FONT="Courier New"]Errors were found while checking the disk drive for /

Press F to attempt to fix the errors, I to ignore, S to skip mounting or M for manual recovery[/FONT]

F doesn't work, and in manual recovery the file system is read-only. How to proceed?

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

Make sure that you identify the toast drive and the new one, it was sda=toast sdb=good before, on the IRC bootscript post. If you still have sda first in the bios then that is a problem as I believe it still has the grub bootloader on it as well.

This script as you might be now realizing is what got a fix to you immediately within 5 min of asking for it and the link to drs305'S chroot grub2 tutorial.

---

### Post by Tanath on 2010-12-09
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   304,576,334   304,576,272  83 Linux
/dev/sda2         304,576,335   312,576,704     8,000,370   5 Extended
/dev/sda5         304,576,398   312,576,704     8,000,307  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    33,559,784    33,559,722  83 Linux
/dev/sdb2          33,559,785    37,752,749     4,192,965  82 Linux swap / Solaris
/dev/sdb3          37,752,750 3,907,024,064 3,869,271,315   5 Extended
/dev/sdb5          37,752,813    41,945,714     4,192,902  83 Linux
/dev/sdb6          41,945,778   310,375,799   268,430,022  83 Linux
/dev/sdb7         310,375,863 3,638,593,979 3,328,218,117  83 Linux
/dev/sdb8       3,638,594,043 3,907,024,064   268,430,022  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a105c1b4-596a-4838-8b95-85ea3f2a491d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9562cf08-68c7-433f-a2c1-0ae93019e319   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3b3b13f0-c1b8-42dd-9189-9ac8474170b2   ext4       root                          
/dev/sdb2        6e93772f-1ef3-4813-8b5c-de861b2c599c   swap       swap                          
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        3c683c2a-490c-4113-8ff4-23bf98f760e6   ext2       tmp                           
/dev/sdb6        6a73e24f-23ac-40f7-87a4-ba1a4acef45b   ext4       home                          
/dev/sdb7        df1af3f4-2a3d-43de-abda-e6c6350361f0   ext4       misc                          
/dev/sdb8        ebb8ca8d-bf86-4a38-b567-46dc06a13c17   ext4       backup                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a105c1b4-596a-4838-8b95-85ea3f2a491d

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
# defoptions=splash vga=791

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
uuid		a105c1b4-596a-4838-8b95-85ea3f2a491d
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d ro splash vga=791 
initrd		/boot/initrd.img-2.6.35-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		a105c1b4-596a-4838-8b95-85ea3f2a491d
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		a105c1b4-596a-4838-8b95-85ea3f2a491d
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d ro splash vga=791 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		a105c1b4-596a-4838-8b95-85ea3f2a491d
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, memtest86+
uuid		a105c1b4-596a-4838-8b95-85ea3f2a491d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9562cf08-68c7-433f-a2c1-0ae93019e319 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  55.6GB: boot/grub/menu.lst
   1.7GB: boot/grub/stage2
 133.8GB: boot/initrd.img-2.6.35-22-generic
  46.4GB: boot/initrd.img-2.6.35-23-generic
 152.9GB: boot/vmlinuz-2.6.35-22-generic
  82.8GB: boot/vmlinuz-2.6.35-23-generic
  46.4GB: initrd.img
 133.8GB: initrd.img.old
  82.8GB: vmlinuz
 152.9GB: vmlinuz.old

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
search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3b3b13f0-c1b8-42dd-9189-9ac8474170b2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=3b3b13f0-c1b8-42dd-9189-9ac8474170b2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=3b3b13f0-c1b8-42dd-9189-9ac8474170b2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=3b3b13f0-c1b8-42dd-9189-9ac8474170b2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3b3b13f0-c1b8-42dd-9189-9ac8474170b2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3b3b13f0-c1b8-42dd-9189-9ac8474170b2 ro single 
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3b3b13f0-c1b8-42dd-9189-9ac8474170b2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10, kernel 2.6.35-23-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a105c1b4-596a-4838-8b95-85ea3f2a491d
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d ro splash vga=791
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a105c1b4-596a-4838-8b95-85ea3f2a491d
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-22-generic (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a105c1b4-596a-4838-8b95-85ea3f2a491d
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d ro splash vga=791
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a105c1b4-596a-4838-8b95-85ea3f2a491d
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=a105c1b4-596a-4838-8b95-85ea3f2a491d ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 10.10, memtest86+ (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a105c1b4-596a-4838-8b95-85ea3f2a491d
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=3b3b13f0-c1b8-42dd-9189-9ac8474170b2  /              ext4         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=6e93772f-1ef3-4813-8b5c-de861b2c599c  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  

/dev/sdb5                                  /tmp           ext2         errors=remount-ro,nosuid    0  0  
/dev/sdb6                                  /home          ext4         defaults                    0  0  

=================== sdb1: Location of files loaded by Grub: ===================


   7.3GB: boot/grub/core.img
  13.7GB: boot/grub/grub.cfg
   6.5GB: boot/grub/stage2
   6.6GB: boot/initrd.img-2.6.35-22-generic
   6.5GB: boot/initrd.img-2.6.35-23-generic
  10.4GB: boot/initrd.img-2.6.35-24-generic
   6.5GB: boot/vmlinuz-2.6.35-22-generic
   6.5GB: boot/vmlinuz-2.6.35-23-generic
   8.4GB: boot/vmlinuz-2.6.35-24-generic
  10.4GB: initrd.img
   6.5GB: initrd.img.old
   8.4GB: vmlinuz
   6.5GB: vmlinuz.old

```

Drives haven't changed. sda (160gb) is the old drive, sdb (2tb) is the new one. The new one is the first drive in the BIOS. Grub seems to be fixed. It updated to show the kernels on both drives.

---

### Post by drs305 on 2010-12-09
Have you tried running fsck from a LiveCD? You can either use Gparted by highlighting sdb1 (your new Ubuntu /) and the Partition, Check, or manually with the following. Make sure the partition is unmounted (no key icon next to the partition listing)).

```
sudo e2fsck -f -y -v /dev/sdb1
```

If that doesn't work, you could temporarily edit the /etc/fstab and change the / line to end in "0 0". You would have to mount /dev/sdb1 and then look for /etc/fstab on the mount point (let us know if you need help). This would disable fsck-ing. It's not something you would want to leave that way but you could see if the system booted.

---

### Post by Tanath on 2010-12-09
As expected, fsck found nothing. It's a brand new drive that's only been partitioned (with gparted) and had files copied over. What exactly would changing the fstab line to have 0 0 do and why wouldn't I want to leave it that way?

---

### Post by wilee-nilee on 2010-12-09
> **drs305 said:**
> Have you tried running fsck from a LiveCD? You can either use Gparted by highlighting sdb1 (your new Ubuntu /) and the Partition, Check, or manually with the following. Make sure the partition is unmounted (no key icon next to the partition listing)).

```
sudo e2fsck -f -y -v /dev/sdb1
```

If that doesn't work, you could temporarily edit the /etc/fstab and change the / line to end in "0 0". You would have to mount /dev/sdb1 and then look for /etc/fstab on the mount point (let us know if you need help). This would disable fsck-ing. It's not something you would want to leave that way but you could see if the system booted.

Did you noticed the grub-legacy, and grub2 in the script, mbr of sda no big deal but it appears to be now mixed together. 

This user had been given your chrootG2 tutorial and had supposedly followed it using a 10.04 thumb booted.

---

### Post by Tanath on 2010-12-09
> **wilee-nilee said:**
> Did you noticed the grub-legacy, and grub2 in the script, mbr of sda no big deal but it appears to be now mixed together. 

This user had been given your chrootG2 tutorial and had supposedly followed it using a 10.04 thumb booted.
Yes, twice, since the first time I ran the purge it automatically reinstalled grub2. And technically it was the 10.04 livecd I'm using now, not a thumb drive. My thumb drive is dying as well. The guide seems to have been a success... unless this is caused by grub, which I don't think it is. I think it has to do with moving to /home and /tmp on separate partitions. The first time it said /tmp wasn't ready.

---

### Post by drs305 on 2010-12-09
> **Tanath said:**
> As expected, fsck found nothing. It's a brand new drive that's only been partitioned (with gparted) and had files copied over. What exactly would changing the fstab line to have 0 0 do and why wouldn't I want to leave it that way?

It disables routine fsck checks. If the system was failing to boot because of an initiated fsck check turning it off may allow the system to boot even if there were errors. 

Leaving it that way would be undesirable because errors would accumulate. Instead of allowing the system to repair smaller errors, they could grow until the system failed.

I assume you are still getting this error?
> Errors were found while checking the disk drive for /

In fstab your /tmp is set to ext2. Is that what it is or is it really ext3 or ext4?

If you need to edit fstab from the CD:
```
sudo mount /dev/sdb1 /mnt
gksu gedit /mnt/etc/fstab

```

---

### Post by wilee-nilee on 2010-12-09
> **Tanath said:**
> Yes, twice, since the first time I ran the purge it automatically reinstalled grub2. And technically it was the 10.04 livecd I'm using now, not a thumb drive. My thumb drive is dying as well. The guide seems to have been a success... unless this is caused by grub, which I don't think it is. I think it has to do with moving to /home and /tmp on separate partitions. The first time it said /tmp wasn't ready.

drs305, and others just know this stuff better, I will have to leave it to them here really.

---

### Post by Tanath on 2010-12-09
> **drs305 said:**
> It disables routine fsck checks. If the system was failing to boot because of an initiated fsck check turning it off may allow the system to boot even if there were errors. 

Leaving it that way would be undesirable because errors would accumulate. Instead of allowing the system to repair smaller errors, they could grow until the system failed.

I assume you are still getting this error?


In fstab your /tmp is set to ext2. Is that what it is or is it really ext3 or ext4?

If you need to edit fstab from the CD:
```
sudo mount /dev/sdb1 /mnt
gksu gedit /mnt/etc/fstab

```
Well, I fscked it with gparted and there were no errors so I don't think it's complaining of a file system error. It would seem to be a problem with fstab or something.

I am still getting the error, and the ext2 partition is my /tmp, yes. I have no trouble chrooting or simply mounting and such with nautilus.

Edit:
OK, thanks for your help thus far wilee-nilee.

---

### Post by Tanath on 2010-12-09
By the way, I don't know if it's relevant or not but I found a post by someone with a similar problem and someone said to change the permissions on /tmp partition to 1777. The user said that fixed his problem so I tried it. Didn't fix the problem, but didn't seem to hurt it either.

Edit:
Sorry, I misdescribed the problem. When I hit F, it then says /tmp is not ready yet or the drive is missing. It then reboots after a few seconds.

Edit again:
In recovery mode I could see this was indeed complaining of file system errors. I suspect it doesn't unmount properly on reboot. Pressing F to fix, and letting it reboot as needed fixes this problem at least temporarily.

---

### Post by drs305 on 2010-12-09
I don't have experience with a separate /tmp folder either. 

Have you tried commenting the /tmp entry in fstab and just letting Ubuntu boot with the /tmp folder created within / ? At least that would tell you if it's something to do with either your fstab entry for /tmp or something in your existing /tmp partition contents.

That's about all I can suggest for this. My Googling apparently turned up the same references regarding permissions but I don't know if that link was appropriate or not.

---

### Post by Tanath on 2010-12-09
I'll try that, thanks. I just noticed I don't have an sdb4, but I read that an extended partition starts at partition 5, so the gap would be expected...

---

### Post by Tanath on 2010-12-09
OK, I tried commenting out the /tmp line in fstab and it changed nothing.

---

### Post by drs305 on 2010-12-09
I Googled "Errors were found while checking the disk drive for /" and found many posts, some marked as SOLVED. Most involved either running the fsck check or mounting the partition and then unmounting it again. Some suggested looking at the drive/partition status using System, Administration, Disk Utility. 

Perhaps you will find a solution in one of those threads. I hope so.

---

### Post by Tanath on 2010-12-09
I've fscked everything to death. The Disk Utility confirms my old drive is subject to imminent failure. I found a post that suggested that Ubuntu has a bug involving a race condition that can cause the /tmp partition problem...

---

### Post by Tanath on 2010-12-09
OK, I've made progress. A few posts said they simply tried rebooting a couple times and things would work, so when I got to the error screen I hit F, let it reboot and proceed to round two. I hit F again and it said something about it possibly taking some time to check the disks (it didn't) and then after a few seconds X came up with a black screen and an error message:

[FONT="Courier New"]Could not update ICEauthority file /var/lib/gdm/.ICEauthority[/FONT]
And another:

[FONT="Courier New"]There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)[/FONT]

It then loaded to the login screen, but the background was back to the default from the spacey one I had changed it to. And there were no users or means to log in. Just the computer icon with the computer name under it.
I switched to a virtual terminal and logged in, confirming that /home and /tmp had mounted properly. I also ran update-grub and update-initramfs -u and I forget exactly what happened next, but I think I pretty much just hit ctrl+alt+del to reboot but I ended up with a kernel panic. It froze with the capslock flashing and the following after errors I didn't catch:

[FONT="Courier New"]Code: 00 00 89 55[/FONT]

After a reboot and another F at the error it went back to X and the two errors repeated dumping me back at the useless login screen.
So, there's new info and new problems... Suggestions?

Edit: The errors I didn't catch were mostly complaining about the file system errors which I think are caused by not unmounting properly at reboots.

---

### Post by Tanath on 2010-12-09
OK, a little more progress. I booted into recovery mode and saw that it was indeed reporting file system errors in /. Seems it frequently doesn't get unmounted properly on reboot. So I hit F... got to terminal and ran a couple commands as per other threads I found:

[FONT="Courier New"]
sudo chown -R gdm: /var/lib/gdm
sudo chown -R tanath: /home/tanath
[/FONT]

I had already tried the 2nd one earlier but ran it again for good measure. Now I don't get the two errors when X starts and the background at the (non-functional) login screen is back to what it was. I still have no userlist though. Suggestions on how to proceed?

---

### Post by Tanath on 2010-12-10
Fixed. The problem was when I copied the system over the permissions weren't preserved. I tried to copy preserving permissions using mc, but it kept failing, so I used Nautilus and it worked, but that didn't preserve permissions properly. I fixed it by reinstalling every package that looked like it might be relevant. Now all seems to be well.

---

