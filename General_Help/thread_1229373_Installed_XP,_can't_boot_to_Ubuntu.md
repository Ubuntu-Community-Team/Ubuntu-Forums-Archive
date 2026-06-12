---
title: "Installed XP, can't boot to Ubuntu"
date: 2009-08-02
forum: General Help
---

### Post by Lord Butters I on 2009-08-02
I installed Windows XP on a separate partition from Ubuntu, but I cannot find a way to boot into Ubuntu.  The XP partition is above the Linux partition, so if I'm correct I could swap their positions and make Ubuntu the partition that is booted into, allowing me to use the Grub bootloader.  However, messing with partitions takes an extremely long time, so I'd rather not do that (and am I even right as to what it will do?)

tl;dnr, how do I boot into Ubuntu when I've installed XP?

---

### Post by merlinus on 2009-08-02
You will have to reinstall grub.  Boot from the live cd, open a terminal and enter

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

and restart.

---

### Post by Lord Butters I on 2009-08-02
Didn't work.  Still boots to XP no matter what I do.

---

### Post by merlinus on 2009-08-02
Do you see the grub menu?  You may have to press Esc very quickly after the initial startup if you do not.

And what, if any, messages did you get when running those commands?

---

### Post by darolu on 2009-08-02
Boot with the LiveCD and open your /boot/grub/menu.lst, paste it here so we can see what the problem is.
Make sure you copy paste the right menu.lst file, should be on /media/disk/boot/grub.menu.lst

Since you already re-installed grub (following merlinus' quick-tutorial) I think you may have the hiddenmenu option enabled, if you see hiddenmenu on your menu.lst file make sure to comment it with "#" at the beginning of the line.

---

### Post by Lord Butters I on 2009-08-02
Here's menu.lst:

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
# kopt=root=UUID=588c5a34-548b-47f6-9f81-777dc4ba48a6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=588c5a34-548b-47f6-9f81-777dc4ba48a6

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
uuid		588c5a34-548b-47f6-9f81-777dc4ba48a6
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=588c5a34-548b-47f6-9f81-777dc4ba48a6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		588c5a34-548b-47f6-9f81-777dc4ba48a6
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=588c5a34-548b-47f6-9f81-777dc4ba48a6 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		588c5a34-548b-47f6-9f81-777dc4ba48a6
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=588c5a34-548b-47f6-9f81-777dc4ba48a6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		588c5a34-548b-47f6-9f81-777dc4ba48a6
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=588c5a34-548b-47f6-9f81-777dc4ba48a6 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		588c5a34-548b-47f6-9f81-777dc4ba48a6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=588c5a34-548b-47f6-9f81-777dc4ba48a6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		588c5a34-548b-47f6-9f81-777dc4ba48a6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=588c5a34-548b-47f6-9f81-777dc4ba48a6 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		588c5a34-548b-47f6-9f81-777dc4ba48a6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by hibliss on 2009-08-02
> **darolu said:**
> Boot with the LiveCD and open your /boot/grub/menu.lst, paste it here so we can see what the problem is.
Make sure you copy paste the right menu.lst file, should be on /media/disk/boot/grub.menu.lst

Since you already re-installed grub (following merlinus' quick-tutorial) I think you may have the hiddenmenu option enabled, if you see hiddenmenu on your menu.lst file make sure to comment it with "#" at the beginning of the line.

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

See that line in your menu.lst file? It needs to be commented. It should look like this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu
```

---

### Post by merlinus on 2009-08-02
# hiddenmenu will certainly be helpful, but notice there is no entry for xp in menu.lst, yet Butters says his machine boots into it upon startup.

Therefore it may be that grub is still not installed correctly.

Again, what messages did you get when running the grub commands?

Allso, post results of

```
sudo fdisk -l
```

---

