---
title: "How to add OS to grub?"
date: 2006-03-05
forum: General Help
---

### Post by thetno on 2006-03-05
I got this Windows XP partition in the partition hdc1.
Ubuntu is installed in hda1.

cat /boot/grub/device.map gives me this

```
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdc
```

I disable hda from bios before installing windows xp in hdc1.
now that i have enabled back after installing windows xp, how to I
add that windows xp boot into grub?

thanks!

my /boot/grub/menu.lst is as follow

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
default		0

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
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.14-ck1 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.14-ck1 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.14-ck1
savedefault
boot

title		Ubuntu, kernel 2.6.14-ck1 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.14-ck1 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.14-ck1
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I tried adding 
```

title 		Windows XP
map		(hd0) (hd2)
map		(hd2) (hd0)
root		(hd2,0)
chainloader+1
makeactive

```

but doesn't work.
nothing happened when i choose that option.

---

### Post by Ocxic on 2006-03-05
try this ```

title 		Windows XP
map		(hd0) (hd2)
map		(hd2) (hd0)
rootnoverify        (hd2,0)
chainloader+1
makeactive
boot       <--- I don't know if this is required but i think it is

```

---

### Post by thetno on 2006-03-05
just tried that,
but somehow, doesn't work
T_T

---

### Post by joshuapurcell on 2006-03-05
This may not be the best way but it works:
Boot up from the Ubuntu install CD, type linux expert at the prompt, then skip all the setting except for installing GRUB. When you go through that step it will automatically search for OSes and add them to the boot list. You can also use this function to install Windows on a computer *after* already having Linux installed when using multiple hard drives (which is the reason I know this works).

---

### Post by lha on 2006-03-05
[QUOTE=Ocxic]try this ```

title 		Windows XP
map		(hd0) (hd2)
map		(hd2) (hd0)
rootnoverify        (hd2,0)
chainloader+1
makeactive
boot       <--- I don't know if this is required but i think it is

```[/QUOTE]

Boot isn't required. You need to replace 'chainloader+1' with 'chainloader +1'. (There must be a space in front of +1.)

---

