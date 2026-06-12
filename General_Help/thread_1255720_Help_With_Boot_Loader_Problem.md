---
title: "Help With Boot Loader Problem"
date: 2009-09-01
forum: General Help
---

### Post by kyle2595 on 2009-09-01
Hi, I have Windows XP and Ubuntu on my computer, And I was Trying to get Ubuntu (a different one than I already have) on to a USB drive. I had messed up and accidentally installed it on my computer's hard drive, I had stopped the installation once I knew that I messed up. Now When I chose "Windows XP" from the grub boot menu that has always been on my computer (Boot Menu 1), it brings me to another boot menu (Boot Menu 2). Boot Menu 2 has the option of "Windows XP" or "Ubuntu". When I select Ubuntu from Boot Menu 2, it brings me back to Boot Menu 1. How do I fix this so that when I select "Windows XP" from Boot Menu 1, it will start Windows and not bring me to Boot Menu 2? Sorry for the confusion, if you can follow what I am trying to say, then it would much appreciated if you can help. Thank you!

---

### Post by blueridgedog on 2009-09-01
What happens when you select Ubuntu from menu 1?  What happens when you select Windows from menu 2?

Can you post the output of:

```
sudo fdisk -l
```

---

### Post by kyle2595 on 2009-09-02
When I select Ubuntu from menu 1 it boots the version of Ubuntu that I have always had on my computer, and when I select Windows from menu 2 it boots up Windows XP.  It had just never had Boot Menu 2 before, it would always boot Windows from Boot Menu 1.  The output of the code is:
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93079307

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5743    46130616    7  HPFS/NTFS
/dev/sda2            5744        7274    12297757+   5  Extended
/dev/sda3            7275        7296      176715   82  Linux swap / Solaris
/dev/sda5            5744        7274    12297726   83  Linux
```Thanks again!

---

### Post by blueridgedog on 2009-09-02
Ok, then we can clean things up since each OS is working.  Can you post the contents of /boot/grub/menu.lst?  You can view it with:

```
gedit /boot/grub/menu.lst
```

---

### Post by louieb on 2009-09-02
Sounds like one of your installs was done with WUBI. Is that right?

---

### Post by kyle2595 on 2009-09-02
Here is the menu.lst:
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
# default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
# timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## Splash image!
splashimage (hd0,4)/boot/grub/images/image.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=0e918612-6152-4c49-90f8-003759e886c4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0e918612-6152-4c49-90f8-003759e886c4

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
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

title        Linux - Ubuntu 9.04
uuid        0e918612-6152-4c49-90f8-003759e886c4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0e918612-6152-4c49-90f8-003759e886c4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux - Ubuntu 9.04 (recovery mode)
uuid        0e918612-6152-4c49-90f8-003759e886c4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0e918612-6152-4c49-90f8-003759e886c4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

# title        Ubuntu 9.04, memtest86+
# uuid        0e918612-6152-4c49-90f8-003759e886c4
# kernel        /boot/memtest86+.bin
# quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title        Other operating systems:
#root
```I had edited it a little in order to use my own splash image or picture for GRUB's backround.

I don't know what WUBI is, is it the installer that is used for installing Ubuntu via Windows?  If so, yes. I think that I installed The first Ubuntu on my computer via Windows XP.  But the version of Ubuntu that I had canceled the installation once I knew that I had screwed up had started to be installed in the demo of Ubuntu from the CD.

---

### Post by louieb on 2009-09-02
Which is menu1 Grub or the Windows boot loader? Think you said Grub but just want to be sure.

Please put the content of c:\boot.ini (the windows XP equivalent of GRUBs menu.lst) in your next post. 

BTW You need to move 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```to between these lines
```

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

```Failure to do so will result in your windows entry being deleted next time there is a kernel update.

---

### Post by kyle2595 on 2009-09-02
Ok, I edited grub like you said, now how do I save it? It says that I don't have permission.

---

### Post by kyle2595 on 2009-09-02
Never mind, I saved it.

---

### Post by kyle2595 on 2009-09-02
Here is the c:/ boot.ini

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr = "Ubuntu"

```

---

### Post by blueridgedog on 2009-09-02
It appears the second install was a wubi one...though I can't help with wubi, you can remove the line "C:\wubildr.mbr = "Ubuntu" from the boot.ini and you will not get a menu when you select windows from within grub.

---

### Post by kyle2595 on 2009-09-02
Thank you all so much! It worked! You all were a big help!
P.S. What is WUBI? Is it bad? I know that it is a .exe file therefore associated with Microsoft.

---

### Post by Vaphell on 2009-09-02
wubi is a tool allowing to install ubuntu inside windows - as far as i know you get Ubuntu entry in add/remove programs, whole OS fits in a single pseudo-partition file existing in windows partition. Generally it's safer option of trying Ubuntu - at least for inexperienced users - than the one including repartitioning (but much slower because of the additional layers of abstraction)

---

### Post by louieb on 2009-09-02
Good to see it fixed. If you'd like to try some other OS in the future I suggest trying VirtualBox Open source edition is in the repository.  But I prefer the PUEL version - both are pretty easy to setup [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

