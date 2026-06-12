---
title: "Messed Up Grub"
date: 2009-08-23
forum: General Help
---

### Post by dm2497 on 2009-08-23
Hey guys,

I have an issue with my grub boot loader. About a week ago I installed kubuntu on my dell vostro 1500 laptop with much success, but decided to get rid of it cause I didn't really like KDE and preffered Gnome alot better. So I installed Ubuntu on my laptop but the grub men still had kubuntu listed cause I deleted the partition. I guess I didn't get rid of it properly. Anyways, I have Ubuntu installed now, and dual-booting with Windows 7, but I updated it the other day to get linux kernel 2.6.28-15, however the boot loader didn't update it keeps saying linux kernel 2.6.28-14. I have a feeling this is because I messed with the "/boot/grub/menu.lst" so I could have the boot order say windows 7 instead of windows vista.  Here's what it looks like.


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
# kopt=root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,0)
savedefault
chainloader	+1

## ## End Default Options ##
## ## End Default Options ##

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,0)
savedefault
chainloader	+1

## ## End Default Options ##
## ## End Default Options ##

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,0)
savedefault
chainloader	+1

## ## End Default Options ##
## ## End Default Options ##

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,0)
savedefault
chainloader	+1

## ## End Default Options ##
```

I was hoping someone could help to reset it so that I have the updated kernel listed, don't have two windows 7 entries, and the unnecessary kernels removed. Any help would be greatly appreciated. Thanks! :)

---

### Post by drs305 on 2009-08-23
If you run "sudo update-grub" the new kernel should be added to menu.lst.

You can do it manually by adding this before the first 'title' section in the bottom part of the menu.lst file (after the "End Default Options" line:
> 
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet



This will be the kernel that boots. If you want the -14 kernel to boot, change the line "default 0" to "default 1".

To add a recovery mode option, copy the -14 recovery mode entry and change the values to -15. Make it the second entry in the section.

---

### Post by dm2497 on 2009-08-23
okay so everytime i tried to update the grub. with ```
sudo update-grub
```it didn't add the new kernel entry into the boot order. it only kept adding windows 7 entries. i also accidently deleted the entire menu.lst file, so i tried to update-grub again to fix and it only added a few things. here's what my menu.lst looks like now.


```

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
# kopt=root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64

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

```

---

### Post by drs305 on 2009-08-23
It looks like you didn't copy the entire file or it got really messed up. Here is what you posted earlier, to which I've added what should be the -15 and -15 recovery options. It will boot to -15. If you want it to boot to -14, change "default 0" to "default 2":

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
# kopt=root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic


title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,0)
savedefault
chainloader	+1


```

---

### Post by oldfred on 2009-08-24
There should only be one  of these lines just before all the choices for Ubuntu - Delete all the others.
## ## End Default Options ##

---

### Post by Monkey.feets on 2009-08-24
ran into the problem with update-grub not updating kernel the other day.  I fixed it by backing up and then deleting menu.lst and then running update-grub to write a new one, after that i commented out the older kernels and added the windows option that i copied from old menu.lst

---

### Post by dm2497 on 2009-08-24
hey guys thanks for the help. i tried the last method and worked awesomely. i deleted the menu.lst and then ran ```
sudo update-grub
```
it then asked me if i would like to generate a new one. I did and it generated one with the updated 15 kernel. I just copy and pasted my old windows option from the code i posted and it works flawlessly. thanks for the help guys. here's the new code for reference. special thanks to Monkey.feets, drs305, and oldfred. 

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64

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

title		Windows 7
rootnoverify	(hd0,0)
savedefault
chainloader	+1

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		9f06ac54-a7e5-48b9-942c-f47d5d2c0c64
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=9f06ac54-a7e5-48b9-942c-f47d5d2c0c64 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by oldfred on 2009-08-24
Next time ubuntu updates the kernel you will lose your windows entry since it is in teh automagic area. You need to move it in between these lines or at the bottom below the end automagic:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

---

### Post by P4man on 2009-08-24
actually, i was wondering about this too. Last time i did an update, it asked me if i wanted to keep my grub menu.lst or replace it with the "package maintainer" version. Since I had a quite customized grub...I kept mine, and added the new kernel manually, but what should I have done ? If say to replace it with a "new one" will it only ADD the new kernel, or pretty much nuke my existing menu.lst?

---

### Post by oldfred on 2009-08-24
It should only update all the entries in the automagic area.  It uses some of the settings in the beginning if you have modified anything and your additions before or after the automagic area should remain.

---

