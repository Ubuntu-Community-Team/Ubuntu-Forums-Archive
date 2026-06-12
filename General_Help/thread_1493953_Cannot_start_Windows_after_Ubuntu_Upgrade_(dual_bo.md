---
title: "Cannot start Windows after Ubuntu Upgrade (dual boot)"
date: 2010-05-26
forum: General Help
---

### Post by jac0117 on 2010-05-26
I just upgraded to the new Ubuntu distribution. My GRUB looks the same and has an entry for WIndows7, however when I chose this option I just get a blank screen and it doesn't load Windows.

Any ideas how to fix this?


jcampos@linux:~$ sudo fdisk -l
[sudo] password for jcampos: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14358   115330603+   7  HPFS/NTFS
/dev/sda2           14359       19456    40949685    f  W95 Ext'd (LBA)
/dev/sda5           14359       19456    40949653+   7  HPFS/NTFS

Disk /dev/sdb: 64.1 GB, 64105742336 bytes
255 heads, 63 sectors/track, 7793 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x72106193

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7335    58918356   83  Linux
/dev/sdb2   *        7340        7470     1052257+   7  HPFS/NTFS
/dev/sdb3            7471        7793     2594497+   5  Extended
/dev/sdb5            7471        7793     2594466   82  Linux swap / Solaris
jcampos@linux:~$ 



////////// here my menu.lst file //////////////////////
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
color cyan/blue white/blue

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

title Microsoft Windows 7
root (hd0,5)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

---

### Post by freddiespagheti on 2010-05-26
Try

```
sudo update-grub
```

If that doesn't work, you could use Super Grub Disk, it solves at least %50 of my boot problems. If you're using grub-legacy, then use the original version (not SGD2). It's (fairly) easy to understand and less buggy.

---

### Post by oldfred on 2010-05-26
On the update did you see instruction to install grub to all drives but check off all drives and partitions? If so you overwrote the windows part that is in the windows partition's boot sector.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If not then post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

