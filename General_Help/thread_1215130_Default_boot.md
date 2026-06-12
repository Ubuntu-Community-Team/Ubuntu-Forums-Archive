---
title: "Default boot"
date: 2009-07-16
forum: General Help
---

### Post by oldtraveler on 2009-07-16
[COLOR="Red"]SOLVED[/COLOR]

]Once again I have outsmarted myself by re-installing Ubuntu 9.04.  The grub loader insists upon making the new Ubuntu the default to load.  I wish to have the Windows boot loader be the default and have edited menu.1st to no avail. 

Here is a copy of menu.1st.  What's wrong please?

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default [color=red]4[/color]
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		[color=red]4[/color]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		04

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
# kopt=root=UUID=1161a518-f455-4d3a-9f94-b068f2cda8cb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1161a518-f455-4d3a-9f94-b068f2cda8cb

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
uuid		1161a518-f455-4d3a-9f94-b068f2cda8cb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1161a518-f455-4d3a-9f94-b068f2cda8cb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		1161a518-f455-4d3a-9f94-b068f2cda8cb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1161a518-f455-4d3a-9f94-b068f2cda8cb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		1161a518-f455-4d3a-9f94-b068f2cda8cb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
[color=red]title		Windows NT/2000/XP (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1[/color]


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb8.
title		linux - PCLINUXOS (on /dev/sdb8)
root		(hd1,7)
kernel		/boot/vmlinuz BOOT_IMAGE=linux_-_PCLINUXOS root=/dev/hdb6 acpi=on resume=/dev/hdb7 vga=791 
initrd		(hd1,5)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb8.
title		failsafe (on /dev/sdb8)
root		(hd1,7)
kernel		/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hdb6 failsafe acpi=on resume=/dev/hdb7 
initrd		(hd1,5)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb8.
title		linux-Xandros (on /dev/sdb8)
root		(hd1,7)
kernel		/boot/vmlinuz BOOT_IMAGE=linux-Xandros root=/dev/hdb8 
initrd		(hd1,5)/boot/initrd.img
savedefault
boot

---

### Post by starcraft.man on 2009-07-16
You can find the answer on how to fix your problem is [here]("http://ubuntuforums.org/showthread.php?t=1214362"), a thread I just responded to yesterday. You can follow either the text editor solution or the GUI one if you prefer.

Your problem if you want to text edit it, is that this: 
```

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 1161a518-f455-4d3a-9f94-b068f2cda8cb
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=1161a518-f455-4d3a-9f94-b068f2cda8cb ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet
```

Is the first entry, instead of the windows entry in red as you highlighted. Move it up to first spot and problem solved. You can also just use the GUI if your not so enclined to manual editting.

And, you should update that machine, if it's jaunty your kernel is old.... we are at least at 13, I just hit 14.

---

### Post by oldtraveler on 2009-07-17
Thank you for your informed and quick reply.  I decided to try StartUp Manager and found it easy to use and effective.  Thus I made no further attempt at editing.

StartUp Manager also has an option to create a rescue boot floppy for GRUB.  I would suppose that one could just as easily create a bootable CD.

Have also run the updates and now have kernel 15.

---

