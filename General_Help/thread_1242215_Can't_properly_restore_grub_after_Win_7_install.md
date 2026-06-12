---
title: "Can't properly restore grub after Win 7 install"
date: 2009-08-16
forum: General Help
---

### Post by Origin on 2009-08-16
Hey guys,

I've followed many instructions found online on how to properly restore grub after installing Windows, but they didn't work.

What happens now: Grub loads when I turn on my laptop, but when I choose any of the Ubuntu options, I'm told file not found.

I have an USB drive that I booted from. It basically is the live CD but on USB. Could that be why?

Additionally, my /boot is on a separate partition than my root (/). Maybe that could be why?

Thanks in advance!

My menu.lst is attached for your convenience:

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
timeout		5

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
# kopt=root=UUID=3f592269-a150-483d-a2dc-8e1a2498a3f6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
root		(hd0,6)
kernel		/vmlinuz-2.6.28-14-generic root=UUID=3f592269-a150-483d-a2dc-8e1a2498a3f6 ro quiet splash 
initrd		/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root		(hd0,6)
kernel		/vmlinuz-2.6.28-14-generic root=UUID=3f592269-a150-483d-a2dc-8e1a2498a3f6 ro  single
initrd		/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,6)
kernel		/vmlinuz-2.6.28-13-generic root=UUID=3f592269-a150-483d-a2dc-8e1a2498a3f6 ro quiet splash 
initrd		/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,6)
kernel		/vmlinuz-2.6.28-13-generic root=UUID=3f592269-a150-483d-a2dc-8e1a2498a3f6 ro  single
initrd		/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,6)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=3f592269-a150-483d-a2dc-8e1a2498a3f6 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,6)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=3f592269-a150-483d-a2dc-8e1a2498a3f6 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,6)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


title		Quick Boot: Puppy Linux 4.00
root		(hd0,6)
kernel		/puppy/vmlinuz root=UUID=3f592269-a150-483d-a2dc-8e1a2498a3f6 vga=normal
initrd		/puppy/initrd.gz
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 7
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by R_W322 on 2009-08-16
My advice would be to back up what you can in Windows 7 then do a clean install of Windows 7 first then do a clean install of Ubuntu.

RYAN.WDZIECZNY

---

### Post by Origin on 2009-08-17
Hm, I fixed it by changing the (hd0,6)s to (hd0,5) in my menu.lst although fdisk returned the boot partition as 6...

Huh

---

### Post by cariboo on 2009-08-17
Next time you run in to the same problem, have a look at this [howto]("http:///ubuntuforums.org/showthread.php?t=224351"), I have used it several time to overcome grub problems.

---

