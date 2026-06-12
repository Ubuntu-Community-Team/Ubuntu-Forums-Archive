---
title: "How to load windows after instaling ubuntu"
date: 2009-09-21
forum: General Help
---

### Post by drakce on 2009-09-21
Hello everyone
I need help to load windows xp sp3 in grub boot loader, and my particion is present on picture.
Problem:
I was have first instaled windows xp, and decided to insta ubuntu, in particion menager i set ubuntu to automatic do instal, but ubuntu made particion spice 2,5 GB. After that i delete particion E on windows and then instal ubuntu again.
After thet i can boot win xp, windows was booting from D partivcion.
If someone can paste me how to edit grub to load windows
My manu list look, and i try every combinations with hd(?,?)
Can someone show me how to edit boot to load win xp, please

menu.lst - See: grub(8), info grub, update-grub(8)
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
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=de0eb40f-dfca-4827-b4ee-2b7419360b35 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de0eb40f-dfca-4827-b4ee-2b7419360b35

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        de0eb40f-dfca-4827-b4ee-2b7419360b35
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=de0eb40f-dfca-4827-b4ee-2b7419360b35 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        de0eb40f-dfca-4827-b4ee-2b7419360b35
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=de0eb40f-dfca-4827-b4ee-2b7419360b35 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        de0eb40f-dfca-4827-b4ee-2b7419360b35
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=de0eb40f-dfca-4827-b4ee-2b7419360b35 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        de0eb40f-dfca-4827-b4ee-2b7419360b35
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=de0eb40f-dfca-4827-b4ee-2b7419360b35 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        de0eb40f-dfca-4827-b4ee-2b7419360b35
kernel        /boot/memtest86+.bin
quiet

title Windows Xpsp3
root (hd0,6)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd0,7)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd0,8)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd0,9)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd1,5)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd1,6)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd1,7)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd2,5)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd1,8)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd1,9)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd2,6)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd2,7)
savedefaul
makeactive
chainloader +1
memtest86+

title Windows Xpsp3
root (hd3,6)
savedefaul
makeactive
chainloader +1
memtest86+

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by sideaway on 2009-09-21
Right click (in gparted) on sda5/6 whichever windows is installed too, and enable the boot flag. hd(1,1) or hd(1,2) depending on which partition is used *MIGHT* work. However, XP generally has to be on the first partition of the table. It's pedantic like that.

---

### Post by drakce on 2009-09-21
Ok,
after doing this did i need to edit menu.lst if is boot for win xp on partition /dev/sda6
and how to edit menu.lst after doing first step

---

### Post by drakce on 2009-09-21
I try to load windows with grub from hd(1,1) and hd(1,2) and grub write me that partition does not exsist,
After i set boot flag nothing happened. 
I still have same problem.
after load from hd(0,6) i got message with error 12 and i can`t load windows again.
help me how to do all what is need to load windows, i am using ubuntu 2 days, i am new.

---

### Post by louieb on 2009-09-21
Get use to using Ubuntu or be prepared to start over.

According to the Gparted screen-shot the PC does not have a boot-able XP install. sda5 and sda6 are the only two partitions that could hold an XP install. 

There are two things about them that tells me  XP can not be made to boot  1) Their both logical partitions - XP need to be install in a primary partition. 2) XP wants the boot flag set on its partition - right now the boot flag is on sda1.    

Is there another hard drive in the computer? It may be your boot-able XP partition is on the other hard drive. In Gparted click the list in the upper right corner and see if another device is listed.

---

### Post by drakce on 2009-09-22
All partition is on one hard disk. Ok, i need to reinstal all sistems ubuntu and XP. Tnx.

---

