---
title: "Starts as low graphics mode"
date: 2009-08-08
forum: General Help
---

### Post by fsdemir on 2009-08-08
I've upgraded my laptop from 8.10 to 9.04 64 bit some time ago. I am not sure about what have gone wrong about upgrading but, hen I've restarted, its GRUB entry was still showing 8.10. It showed 8.10 style boot screen then it could not start and gave me option to start in low graphics mode. When I select that option it warns me about an existing x server in thread 0 and lets me to start in thread 1. It is changed to 9.04 style boot/login theme when started that way. I have an Nvidia chipset and today i tried to upgrade its driver. I got an error about my kernel sources not being in places and it failed. 

What can i do? What extra information should I supply?

---

### Post by wojox on 2009-08-08
Look in /boot/grub/menu.lst. Or post it up here.

---

### Post by fsdemir on 2009-08-08
```
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
timeout		10

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
# kopt=root=UUID=c35eafd6-cd3d-4633-9ca1-e9b6ebd3b637 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c35eafd6-cd3d-4633-9ca1-e9b6ebd3b637

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c35eafd6-cd3d-4633-9ca1-e9b6ebd3b637
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c35eafd6-cd3d-4633-9ca1-e9b6ebd3b637 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c35eafd6-cd3d-4633-9ca1-e9b6ebd3b637
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c35eafd6-cd3d-4633-9ca1-e9b6ebd3b637 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c35eafd6-cd3d-4633-9ca1-e9b6ebd3b637
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
```

---

### Post by fsdemir on 2009-08-08
Yes, I've changed menu.lst to debconf package maintainer version and it worked flawlessly.

Thanks for your help.

---

