---
title: "HELP - Unable to boot Kubuntu or WinXP"
date: 2009-09-22
forum: General Help
---

### Post by SeeJayDee on 2009-09-22
Okay, firstly i gotta let you all know that I'm a total linux newbie.

Installed kubuntu this morning and wanted to set up a dual boot with windows XP. My Disks/partitions are as follows:

hd0,0 - NTFS 320GB with Windows XP installed

hd1,0 - NTFS 809GB, Data

hd3,0 - ext3, 30GB with kubuntu 9.04 installed

hd3,1 - swap, 4.5GB

hd3,2 - FAT32, 40GB, Data

GRUB's menu.lst is located at /boot/grub - I assume it is on hd3,0 but I don't know how to check.

When I let the computer boot by itself, it says 'Load1.5' or something, followed by 'Loading Please Wait...' Then next line says 'ERROR 17' and it does not progress from there.

I have tried using Super Grub Disk. I have no problem booting kubuntu but when I ask it to boot Windows XP it says the following:

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1

Error 13
Invalid or unsupported executable format

...and stops.

I read that grub needs to be on the MBR, problem is I've no idea where the MBR is... (i.e. which disk it is on).

What I want is for the computer to boot up and ask me which OS I want to boot.


anyway here is the content of my menu.lst file, just in case it could be useful.

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
# kopt=root=UUID=96b9f6f5-0b5d-44ba-9d52-464403807891 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=96b9f6f5-0b5d-44ba-9d52-464403807891

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		96b9f6f5-0b5d-44ba-9d52-464403807891
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=96b9f6f5-0b5d-44ba-9d52-464403807891 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		96b9f6f5-0b5d-44ba-9d52-464403807891
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=96b9f6f5-0b5d-44ba-9d52-464403807891 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		96b9f6f5-0b5d-44ba-9d52-464403807891
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Darkwing-Duck on 2009-09-22
Yeah, sounds like a MBR and a GRUB restore problem. I think that this tutorial would be perfect for you.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

I hope this helps you.

---

