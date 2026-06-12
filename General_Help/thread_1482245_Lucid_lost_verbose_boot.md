---
title: "Lucid lost verbose boot?"
date: 2010-05-13
forum: General Help
---

### Post by 2CV67 on 2010-05-13
Hi Guys!

I recently upgraded from 9.10 to 10.04 and seem to have lost my verbose boot in the process.
All I get now is little red dots...

In StartUp-Manager, both "Show boot splash" & "Show text during boot" are checked.
Menu.lst includes #defoptions=splash

Suggestions please?

Thanks!

---

### Post by 2CV67 on 2010-05-14
I rechecked 8.04 (my LTS safety net) & it gives me the same "splash + verbose" boot as 9.10 did.
This is what I like.
10.04 only gives me splash + dots.

My settings in StartUp-Manager & the relevant lines in menu.ist are the same between 8.04 & 10.04

Does 10.04 really have the "splash + verbose" option, or has it been "improved" out?

---

### Post by plucky on 2010-05-14
Did you upgrade or clean install 10.04?

Lucid uses Grub 2 which doesn't use the menu.lst file.

See [link](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

Good Luck

---

### Post by 2CV67 on 2010-05-14
> **plucky said:**
> Did you upgrade or clean install 10.04?

Lucid uses Grub 2 which doesn't use the menu.lst file.

Uh-oh...

As I said above:> I recently upgraded from 9.10 to 10.04 and seem to have lost my verbose boot in the process.
All I get now is little red dots...

I skimmed through the link you kindly attached, which sounds like all kinds of potential disasters!

When I tried```
grub-install -v
```
then I saw```
grub-install (GNU GRUB 0.97)

``` which doesn't sound like Grub2 does it?

---

### Post by plucky on 2010-05-14
> then I saw
Code:

grub-install (GNU GRUB 0.97)

which doesn't sound like Grub2 does it? 

Can you verify that the startup manager changed your menu.lst file?

Post output of ```
cat /boot/grub/menu.lst
```

---

### Post by 2CV67 on 2010-05-16
Thanks for your interest & sorry for the delay in replying.

I checked back on my install/upgrade history.
My original installation was 6.10
I upgraded that to 7.04 then 7.10 then 8.04.
Then I did a clean install of 8.04 (problems with the previous upgrade)
I upgraded that 8.04 to 8.10 then 9.04 then 9.10 & now 10.04
I suppose my Grub 0.97 came with 8.04 then?

In /boot/grub I do have a menu.lst but not a grub.cfg
I have confirmed that StartUp-Manager does change my menu.lst as expected.
When I check "Show text during boot" it removes "quiet" from "defoptions=splash quiet" & from the kernel line "...ro splash quiet".
When I uncheck, it puts quiet back.
But never gives me the verbose boot.

Below is the output from ```
cat /boot/grub/menu.lst
``` as it stands now.

Thanks for any further suggestions!
:::::::::::::::::::::::::::::::::

****@DESKTOP:~$ cat /boot/grub/menu.lst
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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP &#65533;dition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

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
# kopt=root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=splash

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
# howmany=3

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 10.04 LTS, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

#Put in by **** to chainload Ubuntu LTS
title Ubuntu LTS on sda7
root (hd0,6)
chainloader +1

#just the end.



****@DESKTOP:~$

---

### Post by plucky on 2010-05-17
That menu.lst looks correct,all I can suggest is to run ```
sudo update-initramfs -u -k all
``` to generate a new initramfs file,just in case the startup manager didn't create a new file.

Good Luck

---

### Post by 2CV67 on 2010-05-18
I tried ```
sudo update-initramfs -u -k all
``` as you suggested, but no change.

Can somebody confirm that what I am looking for (splash screen, with inset text mode during boot & shut-down) really does still exist with 10.04, like it did with numerous previous versions?

Anybody else able to achieve that with old pre-2 Grub?

Of course, this is not a major problem, just an irritation...

Thanks again for all suggestions.

---

