---
title: "I need help booting into evil windows lol"
date: 2009-12-15
forum: General Help
---

### Post by commodore256 on 2009-12-15
My friend's computer had evil vista, so I rm'd it and installed ubuntu, but he need less evil XP for a killer app that doesn't work in wine. So I installed XP with all of the drivers and edited grub with a live cd and I got ubuntu, but no windows. (but the xp partition is there, I can mount it)

I found a similar problem on the forums, but they didn't explain why that would be the correct number, they just said "change that number to this"

Anyway, I did sudo fdisk -l and got this...

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2527a2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1397       24079   182201197+   5  Extended
/dev/sda2   *       24080       30401    50781465    7  HPFS/NTFS
/dev/sda5            1397        1645     2000061   82  Linux swap / Solaris
/dev/sda6            1646       24079   180201073+  83  Linux

```

This is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=eabb2145-b347-4d94-8fe4-004d8f92a5ca /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a254acca-7747-4fca-92f2-d720a22fe7b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

here's my /boot/grub/menu.lst

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
# kopt=root=UUID=eabb2145-b347-4d94-8fe4-004d8f92a5ca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=eabb2145-b347-4d94-8fe4-004d8f92a5ca

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		eabb2145-b347-4d94-8fe4-004d8f92a5ca
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=eabb2145-b347-4d94-8fe4-004d8f92a5ca ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		eabb2145-b347-4d94-8fe4-004d8f92a5ca
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=eabb2145-b347-4d94-8fe4-004d8f92a5ca ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		eabb2145-b347-4d94-8fe4-004d8f92a5ca
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=eabb2145-b347-4d94-8fe4-004d8f92a5ca ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		eabb2145-b347-4d94-8fe4-004d8f92a5ca
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=eabb2145-b347-4d94-8fe4-004d8f92a5ca ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		eabb2145-b347-4d94-8fe4-004d8f92a5ca
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=eabb2145-b347-4d94-8fe4-004d8f92a5ca ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		eabb2145-b347-4d94-8fe4-004d8f92a5ca
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=eabb2145-b347-4d94-8fe4-004d8f92a5ca ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		eabb2145-b347-4d94-8fe4-004d8f92a5ca
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1

```

As you can see, I was messing with the hda on vista and hoping I would eventually get it right by guessing.

Pleas tell me what I should change it to and why that's the correct number.

---

### Post by tm222 on 2009-12-15
Try adding this before the "### END DEBIAN AUTOMAGIC KERNELS LIST" in menu.lst.
```

title Windows
root (hd0,?)
makeactive
chainloader +1
```

Replace "?" with the partitions /dev thing -1, so /dev/sda9 is probably (hd0,9)

---

### Post by oldfred on 2009-12-15
/dev/sda2   *  is in old grub (hd0,1) change your windows entry to this and see if it boots.

---

### Post by commodore256 on 2009-12-15
Yeah, it was grub 1.xx and it was (hd0,1)

Thanks over 9,000.

---

