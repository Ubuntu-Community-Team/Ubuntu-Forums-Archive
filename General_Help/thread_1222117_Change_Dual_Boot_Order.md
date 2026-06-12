---
title: "Change Dual Boot Order"
date: 2009-07-24
forum: General Help
---

### Post by GeorgeOfTheBush on 2009-07-24
I had installed Ubuntu through WUBI and Windows is the default OS that is highlighted at boot time along with Ubuntu as the second option. **How do I set Ubuntu as the default OS, instead of Windows so that I dont have to manually select Ubuntu everytime I start my PC?**

Here's my /boot/grub/menu.lst

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
# kopt=root=UUID=2D559B75314C23F9 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=2D559B75314C23F9 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=2D559B75314C23F9 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2D559B75314C23F9 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2D559B75314C23F9 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

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
chainloader    +1


```

---

### Post by SuperSonic4 on 2009-07-24
If you remove that "savedefault" (the second line from the bottom) then Linux should be given priority

---

### Post by philcamlin on 2009-07-24
> **SuperSonic4 said:**
> If you remove that "savedefault" (the second line from the bottom) then Linux should be given priority

make a backup of grub first ! :popcorn:

---

### Post by GeorgeOfTheBush on 2009-07-24
Thanks a lot SuperSonic4 and philcamlin for your superquick responses!

Will Removing "savedefault" from the below lines highlight UBUNTU, with Windows as the second option?? I dont want the Windows Option to go way. Just wanted to confirm this before I proceed.

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


---

### Post by SuperSonic4 on 2009-07-24
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
#savedefault
chainloader +1 
```

That removes the default option. I don't run windows any more so I can't verify it against my grub but I get an option to pick either Arch or Arch Fallback. If you want to back up that file you can run ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` and can be restored with```
sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

---

### Post by GeorgeOfTheBush on 2009-07-24
[LIST=1]
[*]I commented out the "savedefault" line
[*]sudo update-grub
[*]Reboot
[/LIST]
**Windows is still highlighted as the first option. Not "Ubuntu".**

---

### Post by merlinus on 2009-07-24
Install startup manager from the repos.  It will allow you to choose which os is default.

---

### Post by GeorgeOfTheBush on 2009-07-25
Installed Startup Manager and selected One of the Linux Kernels as Default OS. However, On boot, Windows is the Default Option that is HIGHLIGHTED.

**I want Ubuntu to be the default selection.**

---

### Post by merlinus on 2009-07-25
This may well be a wubi issue.  FWIW, this situation would not exist if you had installed ubuntu into its own partition with a dual-boot setup.

---

