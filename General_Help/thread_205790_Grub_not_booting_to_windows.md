---
title: "Grub not booting to windows"
date: 2006-06-29
forum: General Help
---

### Post by Skye on 2006-06-29
Hi everyone.

I'm having a problem with grub and booting to windows.  This is all after I've spent a few hours working on the problem, so any help from you guys would be appreciated.

First off, a vocal description of the setup.  I have two hard drives- a Sata disk and an IDE disk.  The Sata disk is the first (and only) sata drive in the system.  The IDE drive is the slave on the primary IDE channel. (It doesn't work when set to master.)  The Sata drive has windows on it, the IDE drive has linux on it.  Grub is installed on the IDE drive.

Grub boots to linux fine- (I'm writing this from Dapper as I speak.)  But, when I try to boot to windows, all it does is print out the grub entry from menu.lst for Windows, alongside some gibberish characters.  In short, it doesn't work, and doesn't give me an error.

The output of fdisk -l is:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3497    28089621   83  Linux
/dev/hdb2            3498        3649     1220940    5  Extended
/dev/hdb5            3498        3649     1220908+  82  Linux swap / Solaris

```

And the menu.lst looks like this:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

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
# kopt=root=/dev/hdb1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other Operating Systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1


title Windows XP
root (hd1,0)
makeactive
chainloader +1

```

If anyone can help me make this work, it would be awesome!

---

### Post by falcon15500 on 2006-06-29
[QUOTE=Skye]title Windows XP
root (hd1,0)
makeactive
chainloader +1
[/QUOTE]

  Am not 100% sure... But shouldn't there be another line at the end with 
```
boot
```???

falc

---

### Post by Skye on 2006-06-29
Well, I tried adding *boot* to the end of the Windows entry in menu.lst, but it didn't work- it printed out the entry for windows (now including boot]) followed by the gibberish again.

Thanks for the attempt, though- any other ideas from anyone?

---

### Post by jazzgossen on 2006-06-29
I'm also only guessing, but how about trying (hd2,0) instead of (hd1,0)?

---

### Post by jharris on 2006-07-03
Hi all, first post here and an Ubuntu user for 5 days now :)

I have a similar problem with my set up. Before installing Ubuntu I originally had two Windows installs, one on my IDE drive which was "C" drive, and the other on my SATA drive which was "D" - this being my main boot drive. After installing Unbuntu on the IDE drive and partitioning it for the linux install, I lost the ability to boot back into either of my Windows installations. I tried booting manually from the cli in GRUB but I kept getting an error saying that there was no NTLDR (or something similar), so being a complete *nix newbie I kind of panicked at the prospect of not being able to boot into Windows (as I'm not yet quite ready to give it up). So in my haste (and lack of understanding) I reformatted my IDE drive and did a clean Ubuntu install (I wasn't concerned about the Windows install on that drive) and hoped that GRUB might auto-detect Windows on the SATA drive - but to no avail. So, the question I ask is, am I screwed, can the problem be resolved by editing GRUB and finally allow me to reboot back into Windows? As I stated before, I am a complete newbie in all things cli and *nix, but I'm prepared to learn and settle in toUbuntu for the long term as I'm loving it too much :) Any help would greatly be appreciated.

-Jason

---

