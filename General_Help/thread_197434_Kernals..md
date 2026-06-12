---
title: "Kernals."
date: 2006-06-15
forum: General Help
---

### Post by BoomAM on 2006-06-15
Hi.
A few days ago i changed the kernal in Ubuntu to the 686 one. So in the boot menu i had the 386 one and the 686 one.
Now today, ive left Ubuntu updating, restarted, and now i have 2 sets of 686 kernals listed?

Whats up with that?

---

### Post by Melvil on 2006-06-15
Yes, the ubuntu devs updated the kern**e**l, so you now have a new one (-25) and and old one (-23)
If the new kernel works fine for you then you can safely remove the old kernel through synaptic or with

*sudo apt-get remove linux-image-2.6.15-23-686*

---

### Post by Arnaud_B on 2006-06-15
just a new version... before it was 2.6.15-23-686 and now 2.6.15-25-686... nothing wrong with that :-) you can uninstall the 386 one if you want as it seems useless now but I would still advise to keep two kernels in case something goes wrong...
A.

---

### Post by BoomAM on 2006-06-15
Thanks for the quick replys guys/gals.

Going off my menu.lst file (see below), what commands would i have put into terminal to remove the old 386 & 686 kernals, whilist keeping the new 386 & 686 ones?

Thanks in advance.

My Menu.lst file says the below:
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
timeout		30

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.15-25-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-25-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-25-686
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		IBM Rescue & Recovery OS
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

On a side note, im really impressed with the community on this forum.
Everyone is really polite and helpful. A far cry from the majority of forums out there.
Well done everyone on here. :D

---

### Post by Melvil on 2006-06-15
Don't mess with the menu.lst! When you remove the linux image (see my command) the menu.lst will be updated for you automatically.
This will remove the old 386/686 kernels and update your grub:

```
sudo apt-get remove linux-image-2.6.15-23-386
sudo apt-get remove linux-image-2.6.15-23-686
```

---

### Post by mlind on 2006-06-15
Or just run 
```

sudo update-grub

```

after removing a kernel. menu.lst should be automatically updated though.

---

### Post by togume on 2006-06-15
Actually, just using sudo apt-get remove linux-image-xxxxxx auto updates the grub menu.lst! Pleasant surprise.

Tomas

---

### Post by BoomAM on 2006-06-16
I only displayed menu.lst above to save me loads of typing. :p

Ive done the 2 previously listed commands, and by the looks of menu.lst its removed the old kernals.
I'll soon see though when i reboot, its just DLing some more updates at the moment.

Thanks for the help though ppl. :)
Much appriciated. :)

---

### Post by scxtt on 2006-06-16
i would leave all WORKING kernels in the /boot directory - you never know when you'll need it :-p ... unless you're really crunched for space, but they're only ~7MB ...

just # them out of your menu.lst ...

---

### Post by BoomAM on 2006-06-16
According to Ubuntu, each kernal is about 70Mb in size.
I fairly sure that 686, 686 Recovery, 386 & 386 Recovery should have me covered in case of kernal failure.
If not, it'll be a good learning experiance for me when it goes belly up. :p

---

