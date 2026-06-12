---
title: "grub help + splash screen trouble"
date: 2009-11-27
forum: General Help
---

### Post by Mathew Roy on 2009-11-27
Hi all,
Every time I update my ubuntu. A new option comes up in the grub boot loader. It displays the older versions of kernel!. I want to see the only the latest one and delete the older versions shown. Hw do I do that?

I have also another trouble!. When I boot normally, the splash screen does not appear only!. The OS works fine but just that the boot screen is missing. The boot screen works fine with the live CD.

I installed UBUNTU in other computers!. but it just works fine on the other computers!..
plz help me out


 my system hardware
Processor   :-intel pentium 4, 2.8ghz
RAM           :-512Mb DDR1
mother brd:-intel 845 GVSR (inbuilt graphics of 64Mb)

---

### Post by raktarok on 2009-11-27
you are using jaunty right? then you can install startupmanager to manipulate grub entries. Or if you are comfortable with editing some files, then just do this:
```
gksudo gedit /boot/grub/menu.lst
```
This file has the menu entries you see during boot time, so just comment out the entries you don't want to see. Be careful though, don't remove other entries!

Or you can remove the old kernel packages. These are the entries you see when you boot. Use synaptic package manager to do this (search for the versions you see in your menu entry.) You can also install ubuntu-tweak, it has the option of removing old kernel packages.


I don't know about the splash screen though. You are talking about the loading screen in jaunty, yes? the one with big letters saying ubuntu... Try using another splash screen (download it from gnome-look) and use the startupmanager to install it.

Hope this helped!

---

### Post by Mathew Roy on 2009-11-29
Thank u for repying!...
sorry I couldn't find a program called "ubuntu-tweak". Plz tell me where I can get it.

> Or you can remove the old kernel packages. These are the entries you see when you boot. Use synaptic package manager to do this (search for the versions you see in your menu entry.)I am a Ubuntu newbie. So can u please explain how to do this!...

---

### Post by raktarok on 2009-11-29
Okay, I will try to give more details this time. :)

Actually, forget about what I said earlier about removing the kernel packages. They may come handy if a new kernel update (meaning a new entry in the grub menu) does not allow you to boot properly. 

First, install the startupmanager (do **sudo apt-get install startupmanager** from aterminal)  and see if it has an option of hiding old menu entries. I use karmic and the program is a bit different in my computer, so I don't know if the jaunty version has this option. Anyway, if it has such an option, you are done, otherwise proceed to the next step. 

Post the contents of /boot/grub/menu.lst here. Do this from a terminal and copy the contents of the file:
```
gksudo gedit /boot/grub/menu.lst
```
Then I will show you how to edit it, so that menu entries are hidden.

You may not be using ubuntu-tweak for removing the kernel entries, but it has tons of other handy features. You can install it by searching for the package name in Synaptic Packet Manager (found in System > Administration) or by just doing this from a terminal:
```
sudo apt-get install ubuntu-tweak
```

---

### Post by Mathew Roy on 2009-12-01
Thank u for helping me. The program "Statrup-manager" was installed successfully. It has a option to limit number of kernals in theboot menu!. I selected it and set it to 1.

---

### Post by Mathew Roy on 2009-12-01
Yes!. It did work!...Now I have only one kernal shown in the grub boot screen!...
But I would like to know what the program had done internally to limit the number of kernels !
Here is the contents of "menu.lst"
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=4bee4b15-5fb8-4742-8c99-e101c2d3bda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4bee4b15-5fb8-4742-8c99-e101c2d3bda4

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
# howmany=1

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        4bee4b15-5fb8-4742-8c99-e101c2d3bda4
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=4bee4b15-5fb8-4742-8c99-e101c2d3bda4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        4bee4b15-5fb8-4742-8c99-e101c2d3bda4
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=4bee4b15-5fb8-4742-8c99-e101c2d3bda4 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, memtest86+
uuid        4bee4b15-5fb8-4742-8c99-e101c2d3bda4
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


```

plz tell me how 2 edit it!..

---

