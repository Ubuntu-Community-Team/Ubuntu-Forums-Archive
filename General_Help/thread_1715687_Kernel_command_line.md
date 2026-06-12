---
title: "Kernel command line"
date: 2011-03-27
forum: General Help
---

### Post by eckeroo on 2011-03-27
I'm trying to implement the following solution from the lm-sensors mailing list:

> 
The bottom line is that you have to add acpi_enforce_resources=no to
the boot command line (in lilo or grub configuration) to get sensors to
work again on this board.

This is for a hardware specific issue, namely the re-activation of on-board sensors for the ASUS A7M266 motherboard.

As there is no grub.conf for UBUNTU 10.10, (my GNU grub version is 0.97), how do I do this?

---

### Post by SeijiSensei on 2011-03-27
The configuration for grub is now in /boot/grub/grub.cfg.  It's marked read-only by default so you'll need to use "sudo chmod u+w /boot/grub/grub.cfg" before editing it (as root again, of course).

---

### Post by mcduck on 2011-03-27
> **eckeroo said:**
> I'm trying to implement the following solution from the lm-sensors mailing list:



This is for a hardware specific issue, namely the re-activation of on-board sensors for the ASUS A7M266 motherboard.

As there is no grub.conf for UBUNTU 10.10, (my GNU grub version is 0.97), how do I do this?

If you are using the legacy Grub instead of Grub2 (which would be the default in Ubuntu 10.10), then Grub configuration file is /boot/grub/menu.lst.

When making the change, remember to not only add it to your current kernel line, but also into the default options section. Otherwise you'll loose the setting during next kernel update.

(if you are actually using Grub2 instead of the legacy Grub, then the configuration file you are looking for is /etc/default/grub, and the option should be added into the "GRUG_CMDLINE_LINUX_DEFAULT" -line.)

> **SeijiSensei said:**
> The configuration for grub is now in /boot/grub/grub.cfg.  It's marked read-only by default so you'll need to use "sudo chmod u+w /boot/grub/grub.cfg" before editing it (as root again, of course).

Grub.cfg shouldn't be edited manually at all, which is why it's set to read-only. Any edits done directly into this file will disappear during kernel updates.

The configuration files that are supposed to be used for editing Grub2 settings are /etc/default/grub and the files in /etc/grub.d/.

---

### Post by eckeroo on 2011-03-27
I need a hand with this:

where exactly do I add the command 'acpi_enforce_resources=no' in my menu.lst file?

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
# kopt=root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro

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

title		Ubuntu 10.10, kernel 2.6.35-28-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.32-29-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-29-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro quiet splash 
initrd		/boot/initrd.img-2.6.32-29-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-29-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-29-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro  single
initrd		/boot/initrd.img-2.6.32-29-generic

title		Ubuntu 10.10, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro quiet splash 
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 10.10, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro  single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 10.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by SeijiSensei on 2011-03-27
Add it to the end of a "kernel" line like this one from the first configuration:

```
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro quiet splash 
```

Just add it after "splash".

---

### Post by mcduck on 2011-03-27
> **SeijiSensei said:**
> Add it to the end of a "kernel" line like this one from the first configuration:

```
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=0af3f2e0-84e0-401e-9014-9277ab21b36a ro quiet splash 
```

Just add it after "splash".

..and to this line as well:

```
# defoptions=quiet splash
```

Otherwise the next kernel update would just make the setting disappear.

---

### Post by eckeroo on 2011-03-28
I can now read my motherboard CPU temperature! A conky display is just incomplete without it.

You guys are totally awesome 8-)

FYI, here's the lm-sensors solution for reactivating the sensors on the ASUS A7M266 motherboard:

[http://lists.lm-sensors.org/pipermail/lm-sensors/2011-March/031970.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2011-March/031970.html)

---

