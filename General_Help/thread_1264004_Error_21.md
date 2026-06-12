---
title: "Error 21"
date: 2009-09-11
forum: General Help
---

### Post by Ioannes on 2009-09-11
Since I install Ubuntu onto a spare hard drive on my PC I have a problem every time I restart the computer from cold. The computer goes through its BIOS routines and as it is to start at the point the Grub menu is displayed it fails and displays "Error 21" but if I press the the computer start button again at this point the computer starts with no problem and displays the menu and will sart in the operating system I select. 

Has anybody seen this before and knows a fix that will avoid the second start to get my system booted into an operation system.

John

---

### Post by Codix121 on 2009-09-11
You mind posting a copy of your grub menu?

TERMINAL:

```
sudo gedit /boot/grub/menu.lst
```


ahh and check out these links:
[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)
[http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/](http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/)


I've never had the error but I'll try looking into it,
I've also heard something about SuperGrub..might wanna google that.

---

### Post by lindsay7 on 2009-09-11
sounds like you computer is trying to start on a drive or usb device first and not the drive with your system on it.

can you post the results of running "sudo fdisk -l"  (the lower case letter L) in the terminal.

---

### Post by Ioannes on 2009-09-14
The Grub file is below:


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
# kopt=root=UUID=5f51bf4e-9db4-4f76-b5e8-43b430c3487e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5f51bf4e-9db4-4f76-b5e8-43b430c3487e

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
uuid		5f51bf4e-9db4-4f76-b5e8-43b430c3487e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=5f51bf4e-9db4-4f76-b5e8-43b430c3487e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		5f51bf4e-9db4-4f76-b5e8-43b430c3487e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=5f51bf4e-9db4-4f76-b5e8-43b430c3487e ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
uuid		5f51bf4e-9db4-4f76-b5e8-43b430c3487e
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=5f51bf4e-9db4-4f76-b5e8-43b430c3487e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid		5f51bf4e-9db4-4f76-b5e8-43b430c3487e
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=5f51bf4e-9db4-4f76-b5e8-43b430c3487e ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
uuid		5f51bf4e-9db4-4f76-b5e8-43b430c3487e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Ioannes on 2009-09-14
The results are below:

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9732    78172258+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc130618c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18891   151741926   83  Linux
/dev/sdb2           18892       19457     4546395    5  Extended
/dev/sdb5           18892       19457     4546363+  82  Linux swap / Solaris
ioannes@ioannes-desktop:~$

---

### Post by oldfred on 2009-09-14
Several years ago I similar problems as I had both sata & pata drives and they did not start up consistently and the MB did not let me choose which HD to boot just hd, cdrom etc.

I converted to UUID's which I see you already have. Perhaps it is because the second drive is not up so the mbr cannot yet find the menu.lst on the second drive? 

I do not have a solution just a possible explanation.

---

### Post by Ioannes on 2009-09-16
Thanks for your help and I think you explanation sounds quite feasible.

John

---

### Post by oldfred on 2009-09-16
More thoughts on your problem. Can you install GRUB to the 2nd harddrive that seems to boot slowly? Then change the order your drives boot in. In newer SATA systems you change boot order in BIOS but older systems with PATA drives you change the jumpers on the HD. The system may be slower to boot everytime as it has to wait for the slow HD to spin up. It may not be a solution but may be worth a try.

---

