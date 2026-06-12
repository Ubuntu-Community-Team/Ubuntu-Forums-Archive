---
title: "Boots in text mode"
date: 2009-08-31
forum: General Help
---

### Post by Vishnu V on 2009-08-31
I have ubuntu 9.04 and now it does not boot in graphical mode mode and i lost it  2 -3 days ago.
the two screen shot of boot up are

---

### Post by x33a on 2009-08-31
post the output of
```
cat /boot/grub/menu.lst
```

---

### Post by tgeer43 on 2009-08-31
Are you saying that it boots up into a complete command line mode with no desktop?
Or are you talking about only the boot process itself?

They are two different issues with distinctly different resolutions.

tgeer

---

### Post by Vishnu V on 2009-08-31
output of cat /boot/grub/menu.lst
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
timeout		03

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
# kopt=root=UUID=7d5a962a-199f-4d55-8866-1d310d3661c7 ro acpi=off noapic xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=7d5a962a-199f-4d55-8866-1d310d3661c7

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

title		ubuntu
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c96d31ef-6da4-4f1e-9413-7948f6f4e3ef ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		ubuntu Safe Mode
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c96d31ef-6da4-4f1e-9413-7948f6f4e3ef ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Memory Test
kernel		/boot/memtest86+.bin  
savedefault
boot

## ## End Default Options ##
### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Waste O S
root	(hd0,1)
savedefault
makeactive
chainloader	+1

title CDROM

root(hd0,5)

kernel /boot/grub/memdisk.bin

initrd /boot/grub/sbootmgr.dsk

quiet

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.


```

---

### Post by Vishnu V on 2009-08-31
I am talking about just the boot process .
I dont have any problem with Desktop

---

### Post by tgeer43 on 2009-08-31
Hmm... Your menu.lst looks ok. The kernel line:
```
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c96d31ef-6da4-4f1e-9413-7948f6f4e3ef ro quiet splash
```has the 'quiet' and 'splash' options so you shouldn't be seeing all the scrolling text.

I'll look into this further but I don't know what to tell you at this point. :confused:

tgeer

---

### Post by Vishnu V on 2009-11-16
I have the same problem in my note book from yesterday
I noticed that it is due to the one of the following 
1.Restore grub after windows installation
or
2.update grub
or
3. Install grub

Any idea ?

thanks

---

### Post by blazemore on 2009-11-16
What about
```
sudo aptitude purge usplash
sudo aptitude install usplash
sudo update-grub

```
That last one's just for luck.

---

### Post by Vishnu V on 2009-11-16
> **blazemore said:**
> What about
```
sudo aptitude purge usplash
sudo aptitude install usplash
sudo update-grub

```
That last one's just for luck.

sorry that doesn't fix the problem

---

