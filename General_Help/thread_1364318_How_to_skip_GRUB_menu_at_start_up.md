---
title: "How to skip GRUB menu at start up?"
date: 2009-12-25
forum: General Help
---

### Post by jac0117 on 2009-12-25
I only have Ubuntu installed on my system, shouldn't the default behavior would be to skip the GRUB menu and boot up directly to Ubuntu? I have my menu.lst file and hiddenmenu is uncommented, also the timeout is set to zero.  Can you help me out? I want to skip the grub menu at start up.  Here's my menu.lst file in case you need it


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
timeout		0

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
# kopt=root=UUID=98ef086c-808c-4976-b19b-284c53012831 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98ef086c-808c-4976-b19b-284c53012831

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
uuid		98ef086c-808c-4976-b19b-284c53012831
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		98ef086c-808c-4976-b19b-284c53012831
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=98ef086c-808c-4976-b19b-284c53012831 ro quiet splash
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		98ef086c-808c-4976-b19b-284c53012831
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=98ef086c-808c-4976-b19b-284c53012831 ro single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-15-generic
uuid		98ef086c-808c-4976-b19b-284c53012831
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=98ef086c-808c-4976-b19b-284c53012831 ro quiet splash
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid		98ef086c-808c-4976-b19b-284c53012831
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=98ef086c-808c-4976-b19b-284c53012831 ro single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.10, memtest86+
uuid		98ef086c-808c-4976-b19b-284c53012831
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

---

### Post by jac0117 on 2009-12-25
Go to System>Administration>Synaptic Package Manager and install startupmanager. Once install it will let you select which kernel to install and the you can also select not to show the grub menu.

the above worked for anyone having this problem.

---

### Post by coffeecat on 2009-12-25
> **jac0117 said:**
> I only have Ubuntu installed on my system, shouldn't the default behavior would be to skip the GRUB menu and boot up directly to Ubuntu? I have my menu.lst file and hiddenmenu is uncommented, also the timeout is set to zero.  Can you help me out? I want to skip the grub menu at start up.  Here's my menu.lst file in case you need it

Very inadvisable to set the timeout to zero. You won't be able to boot into recovery mode if you need to repair your system, and you won't be able to boot into an earlier kernel if a kernel update causes problems. That's why a hidden menu normally has a default of 2 or 3 seconds. It gives you time to hit the esc key to get into the menu.

If you search the forums, you'll find threads by people stymied by Dell's practice of setting up a timeout of zero in their pre-installed Ubuntu machines.

So - sorry I can't help you in the way you want, but think about what I've said.

---

### Post by Leppie on 2009-12-25
you have both grubs installed on your system (did you do a system upgrade?). i suppose it's the grub2 which is showing, as grub legacy chain loads grub2 (according to your menu.lst). the grub2 menu can be hidden by modifying the default settings in /etc/default/grub. to achieve this, make sure that the lines:
```
GRUB_HIDDEN_TIMEOUT=X  ##x seconds to booting default os
GRUB_HIDDEN_TIMEOUT_QUIET=true
```
are not commented out and as coffecat suggested, you may want to set GRUB_HIDDEN_TIMEOUT to 2 or 3.

you may also want to remove one of the two installed grubs ;)

---

