---
title: "[URGENT] cant boot xp"
date: 2009-09-09
forum: General Help
---

### Post by sudoer541 on 2009-09-09
hello i am having problems booting xp.
i have xp on primary master drive and ubuntu on primary slave drive.
when i try to boot xp on grub i get grub error 2.
when i go to bios and set xp as first bootable drive xp boots fine, but it does not give me the option to boot into ubuntu and grub is gone.
i tried restoring grub on xp drive and ubuntu drive but nothing changed. i have attached a copy of my menu.lst```
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
# kopt=root=UUID=acff373e-4cc6-4e49-845c-ed209754a553 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=acff373e-4cc6-4e49-845c-ed209754a553

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        acff373e-4cc6-4e49-845c-ed209754a553
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=acff373e-4cc6-4e49-845c-ed209754a553 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        acff373e-4cc6-4e49-845c-ed209754a553
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=acff373e-4cc6-4e49-845c-ed209754a553 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        acff373e-4cc6-4e49-845c-ed209754a553
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by sudoer541 on 2009-09-09
when i set xp as first bootable drive and use the live cd to restore grub nothing happens, it boots straight to xp. i even tried fixing the mbr by typing fixboot on windows xp repair console, nothing happens.


help is [COLOR=SandyBrown]**[SIZE=4]GREATLY[/SIZE]**[/COLOR] appreciated!

---

### Post by lildigiman on 2009-09-09
windows XP uses ```
fix /mbr
``` If I remember correctly.

---

### Post by sudoer541 on 2009-09-09
> **lildigiman said:**
> windows XP uses ```
fix /mbr
``` If I remember correctly.
when i type fixmbr i get an error message like ????abcdeg1239??? something like that.

---

### Post by sudoer541 on 2009-09-09
those who have xp on primary master, could you please post your menu.lst

---

### Post by earthpigg on 2009-09-09
if it is super duper urgent because there is a critical file or two in windows and you need right now,

try accessing your windows partition from a LiveCD and copying the files onto a thumb drive or your ubuntu partition. that will remove any possibility of permission errors, bypass any problems windows is having, etc.

---

### Post by sudoer541 on 2009-09-09
I booted the live cd and i did: 

```
terminal
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
Error 17: Cannot mount selected partition
 Then I tried
 sudo grub
grub> find /boot/grub/stage1
 (hd1,0)
 grub> root (hd0,0)
 grub> setup (hd0)
 Error 17: Cannot mount selected partition
 grub> root (hd1,0)
 grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  18 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+18 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
 grub> find /boot/grub/stage1
 when I do this nothing changes. I boot ubuntu normally but not windows xp home edition.
 
```

---

### Post by sudoer541 on 2009-09-09
> **earthpigg said:**
> if it is super duper urgent because there is a critical file or two in windows and you need right now,

try accessing your windows partition from a LiveCD and copying the files onto a thumb drive or your ubuntu partition. that will remove any possibility of permission errors, bypass any problems windows is having, etc.


thanks, i just did that. However I want to be able to boot to xp again.
I have some windows only games in there.

---

### Post by sudoer541 on 2009-09-09
i have to swap drives in bios in order to boot ubuntu or xp

---

### Post by confused57 on 2009-09-09
Boot into Ubuntu, then change your entry to boot XP:

```
sudo cp /boot/grub/menu.lst /boot/gru/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```

Try this entry to boot XP from grub:
```
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map         (hd0) (hd1)
map         (hd1) (hd0)
chainloader    +1
```

quit & save...then you "should" be able to boot XP from grub

---

### Post by sudoer541 on 2009-09-10
> **confused57 said:**
> Boot into Ubuntu, then change your entry to boot XP:

```
sudo cp /boot/grub/menu.lst /boot/gru/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```Try this entry to boot XP from grub:
```
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map         (hd0) (hd1)
map         (hd1) (hd0)
chainloader    +1
```quit & save...then you "should" be able to boot XP from grub

ill try that
thanks!

---

### Post by sudoer541 on 2009-09-10
> **confused57 said:**
> Boot into Ubuntu, then change your entry to boot XP:

```
sudo cp /boot/grub/menu.lst /boot/gru/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```Try this entry to boot XP from grub:
```
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map         (hd0) (hd1)
map         (hd1) (hd0)
chainloader    +1
```quit & save...then you "should" be able to boot XP from grub



hey thanks, xp boots fine now.
however, when i boot ubuntu my keyboard and mouse dont work as soon as i reach GDM.

---

### Post by confused57 on 2009-09-10
> **sudoer541 said:**
> hey thanks, xp boots fine now.
however, when i boot ubuntu my keyboard and mouse dont work as soon as i reach GDM.

If you have usb keyboard & mouse, you could try entering your bios setup during boot, then look for an option similar to "usb legacy".

---

### Post by sudoer541 on 2009-09-10
> **confused57 said:**
> If you have usb keyboard & mouse, you could try entering your bios setup during boot, then look for an option similar to "usb legacy".

My keyboard is ps2 <-- whatever they call it and my mouse is the same thing however its connected to a ps2 to usb converter/ hub.

---

### Post by sudoer541 on 2009-09-10
Do you think xorg.conf might be the problem?


here is a copy of my xorg.conf



```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
 Section "Device"
 Identifier	"Configured Video Device"
EndSection
 Section "Monitor"
 Identifier	"Configured Monitor"
EndSection
 Section "Screen"
 Identifier	"Default Screen"
 Monitor		"Configured Monitor"
 Device		"Configured Video Device"
EndSection

```

---

### Post by confused57 on 2009-09-10
I think it probably has something to do with the PS2 to USB converter/hub, you might still check in you bios for a legacy USB setting...I've never used a PS2 to USB(I've used a USB to PS2 with no problems). I wouldn't think it would be your xorg, I don't really know.

Maybe someone else has an idea.

---

### Post by sudoer541 on 2009-09-10
> **confused57 said:**
> I think it probably has something to do with the PS2 to USB converter/hub, you might still check in you bios for a legacy USB setting...I've never used a PS2 to USB(I've used a USB to PS2 with no problems). I wouldn't think it would be your xorg, I don't really know.

Maybe someone else has an idea.

no, I had usb mouse/ hub since the day i bought my computer and it always worked fine with ubuntu until i restored xp by swapping hard drives on menu.lst

any ideas?

---

### Post by sudoer541 on 2009-09-10
anyone? 
any idea how to fix this ?

---

### Post by sudoer541 on 2009-09-11
anyone?

---

