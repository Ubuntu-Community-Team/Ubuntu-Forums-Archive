---
title: "Lost Vista from Grub list"
date: 2009-07-23
forum: General Help
---

### Post by generaltomfoolery on 2009-07-23
I have to use Vista due to work (need to run the School Information Management Database software (so can't just use Ubuntu.

After running the suggested updates in Ubuntu 8.10 today I rebooted to find that Grub had lost Windows Vista.

Can anyone help me get it back please?


Jk

---

### Post by nikhilk on 2009-07-23
> **generaltomfoolery said:**
> I have to use Vista due to work (need to run the School Information Management Database software (so can't just use Ubuntu.

After running the suggested updates in Ubuntu 8.10 today I rebooted to find that Grub had lost Windows Vista.

Can anyone help me get it back please?


Jk

I will again ask for the same things as in this [thread]("http://ubuntuforums.org/showthread.php?t=1220954").

Post the output of
```
sudo fdisk -l
```
and contents of your "/boot/grub/menu.lst" file
```
sudo cat /boot/grub/menu.lst
```

---

### Post by generaltomfoolery on 2009-07-23
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      128488+   6  FAT16
/dev/sda2              17       34417   276319267    7  HPFS/NTFS
/dev/sda3           34418       60801   211929480    5  Extended
/dev/sda5           34418       59726   203294511   83  Linux
/dev/sda6           59727       60801     8634906   82  Linux swap / Solaris
```


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
# kopt=root=UUID=23131f59-5701-43b5-8630-2b6f7635fd8a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=23131f59-5701-43b5-8630-2b6f7635fd8a

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		23131f59-5701-43b5-8630-2b6f7635fd8a
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=23131f59-5701-43b5-8630-2b6f7635fd8a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		23131f59-5701-43b5-8630-2b6f7635fd8a
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=23131f59-5701-43b5-8630-2b6f7635fd8a ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		23131f59-5701-43b5-8630-2b6f7635fd8a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=23131f59-5701-43b5-8630-2b6f7635fd8a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		23131f59-5701-43b5-8630-2b6f7635fd8a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=23131f59-5701-43b5-8630-2b6f7635fd8a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		23131f59-5701-43b5-8630-2b6f7635fd8a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=23131f59-5701-43b5-8630-2b6f7635fd8a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		23131f59-5701-43b5-8630-2b6f7635fd8a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=23131f59-5701-43b5-8630-2b6f7635fd8a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		23131f59-5701-43b5-8630-2b6f7635fd8a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```



The vista bit was me trying something that doesn't work - this bit:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by generaltomfoolery on 2009-07-23
I tried this from the other thread:

> title XP
root (hd0,0)
savedefault
makeactive
chainloader +1

But it did the same - it brings up a DELL diagnostic tool - it doesn't load Vista.

XPS M1530 Dell Laptop.

I think it came about from one of the updates asking about set up of a menu, I thought it meant the start menu.  I think that's where this happened.

---

### Post by generaltomfoolery on 2009-07-23
I solved it!!!!  Yay!

I noticed my ntfs drive (mentioned on your other post) wasn't first so changed the root number.  No idea what it means but it works.  Woop woop!

Here's what I finished with.  Thanks for pointing me in the right direction.

```
title Vista Sucks
root (hd0,1)
savedefault
makeactive
chainloader +1
```

---

### Post by raymondh on 2009-07-23
Congratulations.

Remember that GRUB starts counting from 0. 

Well done.

---

### Post by nikhilk on 2009-07-24
> **generaltomfoolery said:**
> I solved it!!!!  Yay!

I noticed my ntfs drive (mentioned on your other post) wasn't first so changed the root number.  No idea what it means but it works.  Woop woop!

Here's what I finished with.  Thanks for pointing me in the right direction.[/CODE]

Glad you figured it out yourself!

---

