---
title: "reinstallation of GRUB failed"
date: 2006-06-22
forum: General Help
---

### Post by IsKall on 2006-06-22
I tried to reinstall GRUB after my windows installation, but I get this error code:
Code 20.

Anyone who knows what it means? And what I can do about it?

---

### Post by jvl on 2006-06-22
quote from: [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

20 : "Unsupported Multiboot features requested"

This error is returned when the Multiboot features word in the Multiboot header requires a feature that is not recognized. The point of this is that the kernel requires special handling which GRUB is likely unable to provide.

---

### Post by jvl on 2006-06-22
sorry, thought this was boot error. 

what commands are you typing? what partitions do you have? what's in your menu.lst ?

---

### Post by IsKall on 2006-06-22
that doesn't sound good, how do I fix this? :-k

---

### Post by thasheep on 2006-06-22
How are you trying to reinstall grub and when are you getting the error message?

---

### Post by IsKall on 2006-06-22
when I am choosing partition and typing /dev/hda4 (where ubuntu is)

this is my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1    	/media/hda1   	ntfs    auto,gid=1002,umask=0002    0    0
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```



and this is my menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

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
# kopt=root=/dev/hda4 ro

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.15-20-386
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.15-20-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-20-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.15-20-386
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by thasheep on 2006-06-22
Alright, your menu.lst looks fine. I think the problem is you're trying to install to /dev/hda4 when really you should install it to /dev/hda. This is the boot sector of the drive - grub will then load the appropriate partition hda4 (hd0,3) for ubuntu or hda2 (hd0,1) for windows.
Personally, I like to install grub the old fashioned way (by hand). Boot into the dapper live/desktop/install cd (or into ubuntu on your drive if you can). Find a terminal and```
sudo grub
root (hd0,3)
setup (hd0)
exit
```

---

### Post by IsKall on 2006-06-22
on my dapper cd, i can only choose, can't find the terminal

---

### Post by thasheep on 2006-06-22
Is it the Dapper desktop (used to be called live) cd? Applications>Accessories>Terminal
If its the alternate (used to be called install) cd, do <Ctrl><Alt>F2 to get to a virtual terminal (you might have to press enter). If you're doing this, you can type 'grub' instead of 'sudo grub' because you already have root access.

---

### Post by IsKall on 2006-06-22
I can't come in too ubuntu(the grub doesn't work), only windows is booting.

---

### Post by jvl on 2006-06-22
Where exactly do you get the grub error? When you try to boot? 

Is this dualboot machine? Do other operating systems work? Do you know, that you could edit the boot lines in the menu? (I believe it's 'e' key in the menu, then you press 'enter' on the line and can edit it like it's regular commandline. when you're happy with it, you press enter again and boot with the key 'b' )

One more thing to check:

if you have disk hda with partitions hda1 hda4 and hda5, the partition hda5 would be marked in grub as (hd0,2) because it's first disk (counting from zero) and third partition minus one (again, counting from zero). Could this be the problem? 

Could you please post fdisk -l output?

---

