---
title: "Impossible start Ubuntu"
date: 2010-06-28
forum: General Help
---

### Post by mirkko22 on 2010-06-28
hello

I use Ubuntu since version 8.04 and I always upgraded until version 10.4... I am not in dual boot and Window is not installed on my DD (I have only virtuabox in Ubuntu with 2 virtual window installed)...

Today I get a strange issue...I can't start Ubuntu because the grub wont load..After the message Grub Loading I get the Ubuntu logo in middle screen and no more...the process freeze...

I have try to launch a live cd and I am able to get the live deskop where I have test DD and Ram and all seem fine here...

How I can restart my PC ? How I can save my data now ??

Many thank

---

### Post by mirkko22 on 2010-06-28
anybody?

---

### Post by mirkko22 on 2010-06-28
I have use bootinfoscript for see is something is wrong inside partition disk...Here the result...

Any advice ? Thank

```

            
     

============================= Boot Info Summary:
==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive
in 
    partition #1 for /boot/grub.

sda1:
_________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda2:
_________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5:
_________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info:
=============================

Drive: sda ___________________
_____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   306,520,199   306,520,137  83 Linux
/dev/sda2         306,520,200   312,576,704     6,056,505   5 Extended
/dev/sda5         306,520,263   312,576,704     6,056,442  82 Linux swap /
Solaris


blkid -c /dev/null:
____________________________________________________________

Device           UUID                                   TYPE       LABEL       
                 

/dev/loop0                                              squashfs               
                 
/dev/sda1        ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762   ext3                   
                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9c9b99f2-bc0d-4880-9f2d-1d1d91106248   swap                   
                 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output:
===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst:
===========================

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
# Set a timeout, in SEC seconds, before automatically booting the default
entry
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
# kopt=root=UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic
root=UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic
root=UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-21-generic
root=UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-21-generic
root=UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic
root=UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic
root=UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 10.04 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic
root=UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic
root=UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 10.04 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab:
===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>      
<dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ec003f3f-3cac-4dd9-8b0d-de0ad8a5b762 /               ext3   
relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9c9b99f2-bc0d-4880-9f2d-1d1d91106248 none            swap    sw           
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
## usbfs is the USB group in fstab file:
#none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

=================== sda1: Location of files loaded by Grub:
===================


  49.7GB: boot/grub/core.img
  49.7GB: boot/grub/menu.lst
  49.6GB: boot/grub/stage2
  49.7GB: boot/initrd.img-2.6.24-24-generic
  49.7GB: boot/initrd.img-2.6.24-24-generic.bak
  49.8GB: boot/initrd.img-2.6.27-14-generic
  49.8GB: boot/initrd.img-2.6.31-21-generic
  49.6GB: boot/initrd.img-2.6.32-22-generic
  49.7GB: boot/vmlinuz-2.6.24-24-generic
  49.7GB: boot/vmlinuz-2.6.27-14-generic
  49.7GB: boot/vmlinuz-2.6.31-21-generic
  49.7GB: boot/vmlinuz-2.6.32-22-generic
  49.6GB: initrd.img
  49.8GB: initrd.img.old
  49.7GB: vmlinuz
  49.7GB: vmlinuz.old

 
	

```

---

