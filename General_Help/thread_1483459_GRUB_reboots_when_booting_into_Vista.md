---
title: "GRUB reboots when booting into Vista"
date: 2010-05-14
forum: General Help
---

### Post by nickbadal on 2010-05-14
Hi, when I select Vista/Longhorn from my grub list, it shows a black screen, then shows GRUB again. I recently had to reset my menu.lst, so I'm not sure if the settings for the windows option are correct. This is my /boot/grub/menu.lst:
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/Mac4Lin_1.0_GRUB1.xpm.gz

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
# kopt=root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4742b059-51fe-4435-b5ed-8314c36b99f1

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
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro quiet splash
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro quiet splash
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro quiet splash
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro quiet splash
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro quiet splash
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro quiet splash
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-9-rt
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro quiet splash
initrd		/boot/initrd.img-2.6.31-9-rt
quiet

title		Ubuntu 9.10, kernel 2.6.31-9-rt (recovery mode)
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/vmlinuz-2.6.31-9-rt root=UUID=4742b059-51fe-4435-b5ed-8314c36b99f1 ro single
initrd		/boot/initrd.img-2.6.31-9-rt

title		Ubuntu 9.10, memtest86+
uuid		4742b059-51fe-4435-b5ed-8314c36b99f1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Is there anything wrong with this? (yes I know, I have a bunch of kernels haha)

---

### Post by burton247 on 2010-05-14
This is marked as solved, is it actually solved?

---

### Post by nickbadal on 2010-05-14
and I accidentally clicked solved for the thread sorry
still not sure whats wrong with it

---

### Post by burton247 on 2010-05-14
That answered my question. You might wna change that though :P

How many hard drives do you have? and which one is vista installed on? and which partition?

---

### Post by nickbadal on 2010-05-14
well the output for my 'sudo fdisk -l' is:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1313       55208   432914062+   7  HPFS/NTFS
/dev/sda2               1        1312    10538608+   5  Extended
/dev/sda3           55209       77825   181671052+  83  Linux
/dev/sda5               1        1312    10538577   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by burton247 on 2010-05-14
I can't see anything wrong with this. The only difference between mine and yours is that savedefault is before makeactive

---

