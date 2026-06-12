---
title: "GRUB xp error 13"
date: 2006-02-02
forum: General Help
---

### Post by ned.b on 2006-02-02
I have successfully dual booted breezy/xp for a couple of months but have suddenly developed an error when trying to boot to XP.

Error 13: Invalid or unsupported executable format

I have looked through the forums but the problems and fixes seem to be concerned with people dual booting from two hard disks - I have only one.  My menu.lst is as follows:

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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

I can't see anything wrong with it and I can boot successfully to Ubuntu, it is just XP that throws a wobbler.

If anyone has any ideas how I can get the dual boot working successfully again I would be grateful.

---

### Post by Sutekh on 2006-02-02
I can't see anything wrong, perhaps ```
sudo fdisk -l
``` will shed some light.  

I would expect that WinXP and Ubuntu co-existing on the same drive would require Windows to reside in the very first partition (hd0,0), but fdisk will know for sure.

---

### Post by ned.b on 2006-02-02
fdisk -l gives the following:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         528     4241128+  12  Compaq diagnostics
/dev/sda2   *         529        1833    10482412+   7  HPFS/NTFS
/dev/sda3            1834       14959   105434595    f  W95 Ext'd (LBA)
/dev/sda4           14960       30401   124037865   83  Linux
/dev/sda5            1834       14581   102398278+   7  HPFS/NTFS
/dev/sda6           14582       14959     3036253+  82  Linux swap / Solaris

Does that shed any light on the problem? The content of my devices.map is:

(hd0)	/dev/sda

As far as I can work out, sda6 is swap, sda5 is a logical partition under the extended partition of sda3 - used in XP, sda4 is my Ubuntu data partition, sda2 is boot and sda1 is the remnant of something from the original install for this machine.

My setup was that I installed XP on to a 10 gigish partition and had an extended data partition which I mounted into the file system on C:  I then installed Ubuntu which created a swap (82) and the linux (83) partitions. 

Yesterday I was playing with tar and my usb stick - trying to back up files etc - the usb stick stopped responding but I figured it would be ok after a reboot (yes I do work with windows alot)  I don't know if this has anything to do with it, but it is the only thing I can think of.  The subsequent reboot resulted in this problem, USB still not working in Ubuntu, but my priority is getting XP back up from GRUB.

---

### Post by ned.b on 2006-02-02
Looks like user error folks!  After further investigation my tar exploits seem to have rendered my USB stick inoperable - it needed formating to get it usable again.  I also seem to have knackered the XP partition in a similar fashion - the file system was unknown...  and it seemed like such a good idea at the time! :rolleyes:

---

