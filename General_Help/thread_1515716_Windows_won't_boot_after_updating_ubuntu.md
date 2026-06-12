---
title: "Windows won't boot after updating ubuntu"
date: 2010-06-22
forum: General Help
---

### Post by Toshikazu on 2010-06-22
Windows won't boot on Grub after I just updated Ubuntu. I tried to follow the solutions to other people who have had similar problems, but I can't get them to work for me. I am assuming you will want to see this:

silver@silver:~$ sudo fdisk -l
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        3309      979965    5  Extended
/dev/sda3            3310       14593    90638730   83  Linux
/dev/sda5            3188        3309      979933+  82  Linux swap / Solaris

```

When I try to boot windows, the screen goes black for a second and the grub selection screen comes up again. Booting ubuntu is fine though.

---

### Post by Zerocool Djx on 2010-06-22
try and re-install it... 

[http://www.gnu.org/software/grub/grub-download.en.html]("http://www.gnu.org/software/grub/grub-download.en.html%27")

---

### Post by bcbc on 2010-06-22
Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post results back. Instructions in the link.

---

### Post by Toshikazu on 2010-06-23
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 53429789 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot/grub/menu.lst /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 HPFS/NTFS
/dev/sda2          51,199,155    53,159,084     1,959,930   5 Extended
/dev/sda5          51,199,218    53,159,084     1,959,867  82 Linux swap / Solaris
/dev/sda3          53,159,085   234,436,544   181,277,460  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        86C01A4FC01A45B9                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        b3d54b03-45e8-444f-bd5f-43a500757d5c   ext4                                     
/dev/sda5        7e682821-8576-4621-831a-a83dfedf8228   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================



# Sample boot menu configuration file

#



# Boot automatically after a minute.

timeout 60



# By default, boot the second entry.

default 1



# Fallback to the first entry.

fallback 0



title Windows XP

unhide (hd0,0)

rootnoverify (hd0,0)

chainloader +1



# For booting Linux

title  Woody

root (hd0,0)

kernel /boot/vmlinuz-2.4.20-devfs-ntfs-2.1.3

initrd /boot/miniwody1.gz




================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\boot\stage1="GRUB"

C:\ubnldr.mbr="Auto Super Grub Disk"


=================== sda1: Location of files loaded by Grub: ===================


    QtGB: boot/grub/menu.lst

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b3d54b03-45e8-444f-bd5f-43a500757d5c

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		b3d54b03-45e8-444f-bd5f-43a500757d5c
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		b3d54b03-45e8-444f-bd5f-43a500757d5c
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid		b3d54b03-45e8-444f-bd5f-43a500757d5c
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid		b3d54b03-45e8-444f-bd5f-43a500757d5c
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Chainload into GRUB 2
root		b3d54b03-45e8-444f-bd5f-43a500757d5c
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		b3d54b03-45e8-444f-bd5f-43a500757d5c
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set b3d54b03-45e8-444f-bd5f-43a500757d5c
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set b3d54b03-45e8-444f-bd5f-43a500757d5c
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b3d54b03-45e8-444f-bd5f-43a500757d5c
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b3d54b03-45e8-444f-bd5f-43a500757d5c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b3d54b03-45e8-444f-bd5f-43a500757d5c
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b3d54b03-45e8-444f-bd5f-43a500757d5c
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b3d54b03-45e8-444f-bd5f-43a500757d5c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b3d54b03-45e8-444f-bd5f-43a500757d5c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 86c01a4fc01a45b9
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=b3d54b03-45e8-444f-bd5f-43a500757d5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7e682821-8576-4621-831a-a83dfedf8228 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  27.3GB: boot/grub/core.img
  29.9GB: boot/grub/grub.cfg
  30.2GB: boot/grub/menu.lst
  91.3GB: boot/initrd.img-2.6.31-20-generic
  34.7GB: boot/initrd.img-2.6.32-22-generic
  78.8GB: boot/vmlinuz-2.6.31-20-generic
  34.6GB: boot/vmlinuz-2.6.32-22-generic
  34.7GB: initrd.img
  34.6GB: vmlinuz

---

### Post by john newbuntu on 2010-06-23
Please follow the instructions from talsemgeest on "How to restore windows XP bootloader".  Note: You do NOT have to run "fixmbr".
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Only if you do not have the XP installationCD, follow this post by meierfra:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Hopefully that should solve the problem.  Also, just FYI, menu.lst is not used anymore.  Move it away from /boot/grub/menu.lst.

---

### Post by bcbc on 2010-06-23
+1 on the second link for a description of the problem and a fix: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector) 
Testdisk seems to work the best for fixing this problem.

+1: Definitely don't run fixmbr.

---

