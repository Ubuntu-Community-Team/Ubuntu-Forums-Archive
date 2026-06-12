---
title: "lucid lynx long boot time"
date: 2010-07-25
forum: General Help
---

### Post by nbo10 on 2010-07-25
Hi all,
I upgraded to 10.04 and my boot time increased to over 90 seconds. Attached is bootchart output and the results from bootinfoscript. It seems wait-for-root takes almost 30 seconds. Any help on decreasing time? Thanks

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 20483791 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    48,966,119    48,966,057  83 Linux
/dev/sda2          48,966,120   625,137,344   576,171,225   5 Extended
/dev/sda5          48,966,183    56,773,709     7,807,527  82 Linux swap / Solaris
/dev/sda6          56,773,773   625,137,344   568,363,572  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9a1ac5af-c6a4-4fea-b171-479013da8f8a   swap                                     
/dev/sda6        30af95bd-c73c-4c6c-8440-fa14c860c6c3   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext2       (rw,relatime,errors=remount-ro)
/dev/sda6        /home                    ext2       (rw,relatime)


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
default         0

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
# kopt=root=UUID=af9af43c-3337-460c-a600-e292646aebb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=af9af43c-3337-460c-a600-e292646aebb2

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

title		Chainload into GRUB 2
uuid		af9af43c-3337-460c-a600-e292646aebb2
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		af9af43c-3337-460c-a600-e292646aebb2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=af9af43c-3337-460c-a600-e292646aebb2 ro quiet splash
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		af9af43c-3337-460c-a600-e292646aebb2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=af9af43c-3337-460c-a600-e292646aebb2 ro single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
uuid		af9af43c-3337-460c-a600-e292646aebb2
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=af9af43c-3337-460c-a600-e292646aebb2 ro quiet splash
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid		af9af43c-3337-460c-a600-e292646aebb2
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=af9af43c-3337-460c-a600-e292646aebb2 ro single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic
uuid		af9af43c-3337-460c-a600-e292646aebb2
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=af9af43c-3337-460c-a600-e292646aebb2 ro quiet splash
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-19-generic (recovery mode)
uuid		af9af43c-3337-460c-a600-e292646aebb2
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=af9af43c-3337-460c-a600-e292646aebb2 ro single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		af9af43c-3337-460c-a600-e292646aebb2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
	linux	/boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
	linux	/boot/vmlinuz-2.6.31-22-generic root=/dev/sda1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=/dev/sda1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
	linux	/boot/vmlinuz-2.6.28-19-generic root=/dev/sda1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
	echo	'Loading Linux 2.6.28-19-generic ...'
	linux	/boot/vmlinuz-2.6.28-19-generic root=/dev/sda1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set af9af43c-3337-460c-a600-e292646aebb2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=/dev/sda1 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=30af95bd-c73c-4c6c-8440-fa14c860c6c3 /home           ext2    relatime        0       2
# /dev/sda5
UUID=9a1ac5af-c6a4-4fea-b171-479013da8f8a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.4GB: boot/grub/core.img
  10.4GB: boot/grub/grub.cfg
  20.2GB: boot/grub/menu.lst
  20.6GB: boot/initrd.img-2.6.28-19-generic
  20.6GB: boot/initrd.img-2.6.31-22-generic
  20.6GB: boot/initrd.img-2.6.32-24-generic
  22.9GB: boot/vmlinuz-2.6.28-19-generic
  23.0GB: boot/vmlinuz-2.6.31-22-generic
  22.9GB: boot/vmlinuz-2.6.32-24-generic
  20.6GB: initrd.img
  20.6GB: initrd.img.old
  22.9GB: vmlinuz
  23.0GB: vmlinuz.old
```

---

### Post by bakegoodz on 2010-07-25
Any particular reason your using ext2? Ext4 is much faster. Changing realatime to noatime in the /etc/fstab can help especially if your storage system is not good at handling high read and write requests at one time and/or writes slow (usually SDDs)

---

### Post by cj.surrusco on 2010-07-25
There is a bug report about that problem [here]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/498485"). To fix it, I used the same procedure as the guy in post #6.
> I corrected the UUID of the swap partition in /etc/fstab and /etc/initramfs-tools/conf.d/resume so it matched the UUID reported by blkid. Then I ran update-initramfs. After these changes, the long delay is gone.

---

### Post by nbo10 on 2010-07-25
> **cj.surrusco said:**
> There is a bug report about that problem [here]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/498485"). To fix it, I used the same procedure as the guy in post #6.

The UUID is correct in fstab and /etc/initramfs-tools/conf.d/resume so that doesn't seem to be the problem.


ext2 is what I picked many years back when I first formatted the drive.

---

