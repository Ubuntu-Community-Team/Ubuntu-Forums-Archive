---
title: "GRUB read error - and partition mess"
date: 2011-02-18
forum: General Help
---

### Post by AvalonSpirit on 2011-02-18
Hey,

I'm having problems booting my computer.
I turn on my computer and get a grub message:

GRUB read error

So I turn it off and on again a few times until it eventually will boot.
I've tried things on other threads i've read and from the GRUB community documentation page: 

[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#Reinstalling%20from%20LiveCD)

I dont know what the problem is, however I think I cant solve it due to the partition mess I've made of my hard drives.

I have a multiboot system with 2 hard drives,

sda: has windows vista on sda2 and Debian on sda3, and a windows recovery partition on sda1

sdb: has ubuntu 10.10 on sdb1 and kubuntu 10.10 on sdb6 (sdb[7-8] are swap partition and sdb2 is an extended partition type, whatever that is... hehe)

I installed kubuntu while trying to solve the problem hoping it would rewrite the MBR with its GRUB.

The grub that is currently working is the one on the Debian system which was the last one I installed before kubuntu (I dont think it has GRUB 2 though)

Any help would be greatly appreciated!
thanks

---

### Post by Quackers on 2011-02-18
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by AvalonSpirit on 2011-02-18
Ok, here we go,
this is the RESULTS.txt file:

Hope this helps, Thanks!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   568,178,708   568,178,646  83 Linux
/dev/sdb2         568,180,734   976,768,064   408,587,331   5 Extended
/dev/sdb5         964,880,028   976,768,064    11,888,037  82 Linux swap / Solaris
/dev/sdb6         568,180,736   952,991,743   384,811,008  83 Linux
/dev/sdb7         952,993,792   964,878,335    11,884,544  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sdb1        baa53def-f8d2-4ff0-896b-e0e1c7c44f49   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5                                               swap                                     
/dev/sdb6        73807f8a-207a-44dd-a987-962fb57edd8c   ext4                                     
/dev/sdb7        5b9dbaab-9c5c-45af-b4a0-dfe9f1d5662b   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=baa53def-f8d2-4ff0-896b-e0e1c7c44f49

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

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.31-17-generic
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-17-generic (recovery mode)
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.10, kernel 2.6.28-17-generic
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 10.10, kernel 2.6.28-17-generic (recovery mode)
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 10.10, kernel 2.6.27-14-generic
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 10.10, kernel 2.6.27-14-generic (recovery mode)
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 10.10, kernel 2.6.27-11-generic
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 10.10, kernel 2.6.27-11-generic (recovery mode)
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 10.10, kernel 2.6.27-9-generic
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 10.10, kernel 2.6.27-9-generic (recovery mode)
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 10.10, kernel 2.6.27-7-generic
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 10.10, kernel 2.6.27-7-generic (recovery mode)
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 10.10, memtest86+
uuid		baa53def-f8d2-4ff0-896b-e0e1c7c44f49
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows Vista/Longhorn (loader)
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
/dev/sdb5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.8GB: boot/grub/menu.lst
   5.9GB: boot/grub/stage2
   6.0GB: boot/initrd.img-2.6.27-11-generic
   6.0GB: boot/initrd.img-2.6.27-14-generic
   6.0GB: boot/initrd.img-2.6.27-7-generic
   6.0GB: boot/initrd.img-2.6.27-9-generic
   5.9GB: boot/initrd.img-2.6.28-17-generic
   5.9GB: boot/initrd.img-2.6.31-17-generic
   6.0GB: boot/initrd.img-2.6.35-24-generic
   6.0GB: boot/initrd.img-2.6.35-25-generic
   6.0GB: boot/vmlinuz-2.6.27-11-generic
   6.0GB: boot/vmlinuz-2.6.27-14-generic
   6.0GB: boot/vmlinuz-2.6.27-7-generic
   6.0GB: boot/vmlinuz-2.6.27-9-generic
   6.0GB: boot/vmlinuz-2.6.28-17-generic
   5.9GB: boot/vmlinuz-2.6.31-17-generic
   6.0GB: boot/vmlinuz-2.6.35-24-generic
   6.0GB: boot/vmlinuz-2.6.35-25-generic
   6.0GB: initrd.img
   6.0GB: initrd.img.old
   6.0GB: vmlinuz
   6.0GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 73807f8a-207a-44dd-a987-962fb57edd8c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 73807f8a-207a-44dd-a987-962fb57edd8c
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
	search --no-floppy --fs-uuid --set 73807f8a-207a-44dd-a987-962fb57edd8c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=73807f8a-207a-44dd-a987-962fb57edd8c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 73807f8a-207a-44dd-a987-962fb57edd8c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=73807f8a-207a-44dd-a987-962fb57edd8c ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 73807f8a-207a-44dd-a987-962fb57edd8c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 73807f8a-207a-44dd-a987-962fb57edd8c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10, kernel 2.6.35-25-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-24-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.31-17-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.28-17-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.28-17-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro single
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.27-14-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro single
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.27-11-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.27-9-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.27-9-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash
	initrd /boot/initrd.img-2.6.27-9-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.27-9-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro single
	initrd /boot/initrd.img-2.6.27-9-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.27-7-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro quiet splash
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 10.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=baa53def-f8d2-4ff0-896b-e0e1c7c44f49 ro single
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 10.10, memtest86+ (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set baa53def-f8d2-4ff0-896b-e0e1c7c44f49
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=73807f8a-207a-44dd-a987-962fb57edd8c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=5b9dbaab-9c5c-45af-b4a0-dfe9f1d5662b none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


 359.8GB: boot/grub/core.img
 295.4GB: boot/grub/grub.cfg
 291.3GB: boot/initrd.img-2.6.35-22-generic
 359.8GB: boot/vmlinuz-2.6.35-22-generic
 291.3GB: initrd.img
 359.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda1: Input/output error
hexdump: /dev/sda1: Input/output error
hexdump: /dev/sda2: Input/output error
hexdump: /dev/sda2: Input/output error
hexdump: /dev/sda3: Input/output error
hexdump: /dev/sda3: Input/output error
hexdump: /dev/sda4: Input/output error
hexdump: /dev/sda4: Input/output error
```

Edit:

Forgot to mention that I ran the script from the ubuntu system as the Live CD I have right now (kubuntu) does not want to recognize my wireless card.
From what I saw on SF i don't think it matters much, right?

---

### Post by AvalonSpirit on 2011-02-25
Ok, I kept trying to use grub-update related commands without any results.
I changed the boot order of the harddrives in the BIOS, so that the one with ubuntu and kubuntu goes first. Now I can boot and use my computer again, however when I try to boot to the other harddrive i still get the Grub read error (sometimes I get error 25 or 17, along with an attempt to load stage 1.5)

---

