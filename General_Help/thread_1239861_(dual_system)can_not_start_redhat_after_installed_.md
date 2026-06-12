---
title: "(dual system)can not start redhat after installed Ubuntu 9.04"
date: 2009-08-14
forum: General Help
---

### Post by adameye on 2009-08-14
I searched from website, somebody said: 
[http://www.unix.com/ubuntu/48140-make-ubuntu-red-hat-boot-partitions.html](http://www.unix.com/ubuntu/48140-make-ubuntu-red-hat-boot-partitions.html)
"[COLOR="Red"]GRUB couldn't possibly keep all its settings in the tiny amount of space a boot sector gives, it's actually smart enough to understand some partition types, to let it reach in and grab a config file. Usually /boot/grub/grub.conf, whichever partition that ended up at in your file tree. It'll be reading the new grub.conf instead of the old one now, but if you can get your old one, you can add settings from it to your new one[/COLOR]"

but the problem is: I did not keep the old menu.lst of the redhat! how can I find it if I can not log in now? Is there any way I can check the menu.lst of redhat from ubuntu?

thanks!

---

### Post by gabry79Italy on 2009-08-14
post me back output of code:
sudo fdisk -l
and output of code
cat /boot/grub/menu.lst

---

### Post by adameye on 2009-08-14
sudo fdisk -l
[COLOR="Red"]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008b875

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14         267     2040255   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e2bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1816    14586988+  83  Linux
/dev/sdb2            1817       33791   256839187+   5  Extended
/dev/sdb5            1817        2789     7815559+  82  Linux swap / Solaris
/dev/sdb6            2790       33791   249023533+  83  Linux

[/COLOR]
cat /boot/grub/menu.lst

[COLOR="Red"]
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
# kopt=root=UUID=2c01fbd2-a24c-474d-a55a-583297b9b22c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2c01fbd2-a24c-474d-a55a-583297b9b22c

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		2c01fbd2-a24c-474d-a55a-583297b9b22c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c01fbd2-a24c-474d-a55a-583297b9b22c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		2c01fbd2-a24c-474d-a55a-583297b9b22c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c01fbd2-a24c-474d-a55a-583297b9b22c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		2c01fbd2-a24c-474d-a55a-583297b9b22c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


[/COLOR]


> **gabry79Italy said:**
> post me back output of code:
sudo fdisk -l
and output of code
cat /boot/grub/menu.lst

thanks!

---

### Post by gabry79Italy on 2009-08-14
And after '### END DEBIAN AUTOMAGIC' is there nothing?
Aren' there any titles referring red hat????? 
Give me back output of code
ls /media
Sorry for my bad English, I hope you understand my words

---

### Post by adameye on 2009-08-14
no more titles, I have tried to use hd0,0 for redhat to start but i failed
 
ls /media
[COLOR="Red"]cdrom  cdrom0  floppy  floppy0[/COLOR]

thanks


> **gabry79Italy said:**
> And after '### END DEBIAN AUTOMAGIC' is there nothing?
Aren' there any titles referring red hat????? 
Give me back output of code
ls /media
Sorry for my bad English, I hope you understand my words

---

### Post by louieb on 2009-08-14
Should be easy enough once You know which partition holds Red Hat and which partition hods Ubuntu.  (looks like any 2 of 3). 

Please follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and put the results.txt file in your next post (use code tags - lts long).  Note instructions say to use from live CD - but you can do it from your  Ubuntu hard drive install.

Kind of surprised the Ubuntu installer did not find the Red Hat install and include it automatically.

---

### Post by adameye on 2009-08-17
thanks, I will try it, but is there any easy step 
I can find which partition without using CD, maybe I should just try hd1,or hd2
> **louieb said:**
> Should be easy enough once You know which partition holds Red Hat and which partition hods Ubuntu.  (looks like any 2 of 3). 

Please follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and put the results.txt file in your next post (use code tags - lts long).  Note instructions say to use from live CD - but you can do it from your  Ubuntu hard drive install.

Kind of surprised the Ubuntu installer did not find the Red Hat install and include it automatically.

---

### Post by louieb on 2009-08-17
Running the script from your Ubuntu install is the easy way.

Without the information provided by the script anything I could suggest would be just a guess.

---

