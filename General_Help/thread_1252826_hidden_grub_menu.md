---
title: "hidden grub menu"
date: 2009-08-29
forum: General Help
---

### Post by AmerNewbieInDE on 2009-08-29
i have vista and ubuntu on the same notebook, i am adding users and i want to hide part of the boot menu, how do i do this, i tried but failed... 

I want only ubuntu and vista to show on the boot list...

here is my menu.lst

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
# kopt=root=UUID=2a974aa0-32dc-4656-b8cf-5da7f737127f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2a974aa0-32dc-4656-b8cf-5da7f737127f

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

title        Ubuntu 9.04
uuid        2a974aa0-32dc-4656-b8cf-5da7f737127f
kernel        /boot/vmlinuz-2.6.31-020631rc5-generic root=UUID=2a974aa0-32dc-4656-b8cf-5da7f737127f ro quiet splash 
initrd        /boot/initrd.img-2.6.31-020631rc5-generic

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

hiddenmenu

quiet

title        Ubuntu 9.04, kernel 2.6.31-020631rc5-generic (recovery mode)
uuid        2a974aa0-32dc-4656-b8cf-5da7f737127f
kernel        /boot/vmlinuz-2.6.31-020631rc5-generic root=UUID=2a974aa0-32dc-4656-b8cf-5da7f737127f ro  single
initrd        /boot/initrd.img-2.6.31-020631rc5-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        2a974aa0-32dc-4656-b8cf-5da7f737127f
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2a974aa0-32dc-4656-b8cf-5da7f737127f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        2a974aa0-32dc-4656-b8cf-5da7f737127f
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2a974aa0-32dc-4656-b8cf-5da7f737127f ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2a974aa0-32dc-4656-b8cf-5da7f737127f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2a974aa0-32dc-4656-b8cf-5da7f737127f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2a974aa0-32dc-4656-b8cf-5da7f737127f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2a974aa0-32dc-4656-b8cf-5da7f737127f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2a974aa0-32dc-4656-b8cf-5da7f737127f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

---

### Post by drs305 on 2009-08-29
So you want to hide the recovery modes and memtest86+ ?

An easy way is to use StartUp-Manager - a GUI app that lets you tweak lots of grub settings. The two mentioned above are in the Advanced Options tab.

The 'SUM' guide linked to in my signature line explains how to install and run StartUp-Manager. It will edit menu.lst and do the things you want accomplished.

If you want to edit menu.lst manually, just put a # symbol in front of all the menu items you don't want displayed (all lines in each section - 4-5 lines each in your example). For example:
> 
# title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
# uuid 2a974aa0-32dc-4656-b8cf-5da7f737127f
# kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=2a974aa0-32dc-4656-b8cf-5da7f737127f ro single
# initrd /boot/initrd.img-2.6.28-11-generic

---

### Post by AmerNewbieInDE on 2009-08-29
if i use the # am i still able to (esc) and get the menu?

---

### Post by diafanos on 2009-08-29
no. if you want to hide grub menu, then just uncomment the #hiddenmenu line.
After that if you want to see the grub menu, you have to press esc. 

On the other hand, if you comment out the menu items, as drs305 said, you won't be able to see them no matter what.

---

### Post by AmerNewbieInDE on 2009-08-29
> **diafanos said:**
> no. if you want to hide grub menu, then just uncomment the #hiddenmenu line.
After that if you want to see the grub menu, you have to press esc. 

On the other hand, if you comment out the menu items, as drs305 said, you won't be able to see them no matter what.

so what you say, either all is hidden or none is hidden?? i what to give users the choice of ubuntu or linus.. but not all of the boot menu..

---

### Post by drs305 on 2009-08-29
> **AmerNewbieInDE said:**
> so what you say, either all is hidden or none is hidden?? i what to give users the choice of ubuntu or linus.. but not all of the boot menu..

Yes. The grub menu appears before Ubuntu 'knows' who the user is, so all users get the same access from the menu during boot.

I am not familiar with accessibility features but I know Ubuntu has introduced options which allow limited access - it is just not through the grub menu. Perhaps other posters will be able to contribute information about how this is done.

---

### Post by AmerNewbieInDE on 2009-08-29
yes, i know grub loads before linux knows who it is...thank you anyways. i was just hoping to give everyone the option of "windows" or "Ubuntu", but if i need, i could esc or some other command and get the rest of the options...

---

### Post by diafanos on 2009-08-30
No there is not such functionality in grub. The only thing that you can do is to rearrange the boot entries and add some comments in order to help other users to select what they really want. e.g., you can create the following menu:

Main Operating Systems:
1. Ubuntu
2. Windows

Just for debug reasons. Stay away, please:
3. Ubuntu 9.04 2.19....
4. old-Ubuntu smth...
5. Memory test..
....
etc

---

