---
title: "grub modification"
date: 2009-08-20
forum: General Help
---

### Post by j_arquimbau on 2009-08-20
Hello.

I installed ideneb on my computer and afterwards I installed ubuntu. The OsX partition didn't appear on the grub menu, so I edited /boot/grub/menu.lst and added the OsX partition. 

I forgot to say that I had previously installed Vista.

The problem is that then my grub menu was kind of:

Windows Vista (loader)
Ubuntu
Ubundu rescue
Ubuntu memlist
Windows Vista (loader)
OsX

(I have written it as I remember. Might not be the exact words but the order is correct).

As the OsX didn't work I edited menu.lst again and deleted it, but I still have two Vista loaders. I can't find the error at the menu.lst file. 
I post it here:

---------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry numbe# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
r NUM. Numbering starts from 0, and
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
#      password --###############################/
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
# kopt=root=UUID=8825c815-7b2f-######################### ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=#####################################

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
uuid		#####################################
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID= ################### ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		#########################################
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=########################### ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		##############################################
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID= ############################## ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		####################################
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID= ############################## ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		################################################
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---------------------------------------------------------------------

Does anybody now what is the mistake here or how I could reinstall grub correctly?? 

I've tried:

$ sudo grub
grub> find /boot/grub/stage1
grub> root (hd0,4)
grub> setup (hd0)
grub> quit

but didn't work.

Thank you very much

PS: I've erased some numbers which I don't know what they are for but, just in case!

---

### Post by tgeer43 on 2009-08-20
You don't say what the problem is that you are trying to correct. If it's the fact that you have two entries for Vista then simply delete the first one which is right near the top of the file.

If you are talking about something else then please specify.

tgeer

---

### Post by j_arquimbau on 2009-08-20
> **tgeer43 said:**
> You don't say what the problem is that you are trying to correct. If it's the fact that you have two entries for Vista then simply delete the first one which is right near the top of the file.

If you are talking about something else then please specify.

tgeer

mmm OK! That was the problem and now I feel really stupid because I looked for something like that several times and didn't find it.

Thank you.

---

### Post by tgeer43 on 2009-08-21
You are welcome and no need to feel stupid. We are all here to help each other. That's one of the things that makes Ubuntu so great.

tgeer

p.s. I make really obvious errors all of the time.

---

