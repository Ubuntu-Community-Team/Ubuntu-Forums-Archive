---
title: "&quot;Missing operating system.&quot; (grub issue? LVPM...)"
date: 2009-12-24
forum: General Help
---

### Post by Gizenshya on 2009-12-24
I used LVPM to convert my wubi install to full.  I finally had to use qtparted from a LiveCD to get it formatted, but I did it.

After LVPM finished, it said restart to the drive.  I did and I got this:  "Missing operating system."  It didn't give any information or options.

what do I do?

---

### Post by Gizenshya on 2009-12-27
Here is some more info...

this is the menu.lst file from the new drive:

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
timeout 	10

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
# kopt=root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
# defoptions=quiet splash all_generic_ide

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro quiet splash all_generic_ide 
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro quiet splash all_generic_ide 
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro quiet splash all_generic_ide 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-3-rt
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro quiet splash all_generic_ide 
initrd		/boot/initrd.img-2.6.28-3-rt

title		Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro  single
initrd		/boot/initrd.img-2.6.28-3-rt

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro quiet splash all_generic_ide 
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-23-rt
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro quiet splash all_generic_ide 
initrd		/boot/initrd.img-2.6.24-23-rt

title		Ubuntu 9.04, kernel 2.6.24-23-rt (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro  single
initrd		/boot/initrd.img-2.6.24-23-rt

title		Ubuntu 9.04, kernel 2.6.24-23-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro quiet splash all_generic_ide 
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro quiet splash all_generic_ide 
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d6e56fd2-24b0-4a32-939b-5b9072233687  ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 9.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1


title UNetbootin-partitionmanagerrev146
   root (hd0,)
   kernel /ubuntu/disks/boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram
   initrd /ubuntu/disks/boot/ubninit
   boot


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,0)
makeactive
chainloader +1
boot


title Windows Vista (loader)
root (hd0,0)
makeactive
chainloader +1
boot


title Windows NT/2000/XP (loader)
root (hd1,0)
makeactive
chainloader +1
boot


```

I see vista there.  But Ubuntu is alone on that drive now.  Is the reason it isn't finding Ubuntu because It's trying to find Vista?  I have no idea how to modify that.  I've never done anything with grub, and I have no idea where to begin (or what most of that means).  I'm not afraid to modify the grub stuff, though.. 1.  It isn't working anyway.  2.  I have the menu.lst file completely right there, so I could just copy it back.  3.  Everything on that drive is backed up, and I can just reformat and re-copy if anything fails.  So I can try any wild guesses any of you have.

this is that drive's output from fdisk -l.  It is sdc, and 2 partitions-- ext3 and swap.

```
Disk /dev/sdc: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2168    17408000+  83  Linux
/dev/sdc2            2169        2431     2112547+  82  Linux swap / Solaris
```

I mounted the drive from the original wubi install, and all the files are in that ext3 partition that should be, as far as I can tell.

---

### Post by Gizenshya on 2009-12-28
bump

anyone? :'(

---

### Post by ppb1701 on 2009-12-28
I did this over the weekend.

you have to change root ()/ubuntu/disks to something like root(hd0,0) in that menu.lst   first 0 is which physical hard drive, second 0 is which physical partition.  zeros should be the the first one.  looks like at the moment you still have the drive uuid's somewhere along the way I had to re-add those.

once those line up it should be able to boot it.

sudo blkid
will give you the uuid, and should list the partition

---

### Post by ppb1701 on 2009-12-28
oh yeah fstab (/etc/fstab) may lose any uuid it has as well, I had to re-add my swap files, though I'm not really sure why it had one listed in the parameters and the others did not.

---

