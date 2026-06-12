---
title: "Ubuntu no longer appears in GRUB boot menu"
date: 2009-07-29
forum: General Help
---

### Post by Cfhs_1 on 2009-07-29
I installed windows 7 to a separate partition on my hard drive (Works like a charm, props to Microsoft for finally getting it right) then reinstalled grub to the MBR. everything was happy and fine until I decided I didn't like the crowded boot menu, So I attempted to remove ubuntu (recovery mode) and ubuntu (memtest) form the boot menu, but I accidentally removed ubuntu from the list too! now all that appears in grub is windows 7. The worst part is In all my rushing I forgot to make a backup copy of my menu.1st file. So now I need you, oh amazing gurus of Ubuntu goodness, to help me put ubuntu back in to my grub boot list. below is what my menu.1st file looks like in it's current state.

__________________________________________________________________________


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
timeout		30

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
# kopt=root=UUID=72cec832-188b-40b6-9c41-18fb8b5dd39e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=72cec832-188b-40b6-9c41-18fb8b5dd39e

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


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7 Ultimate
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by frunns on 2009-07-29
This might not be the most awesome way to do it, but if you boot up the live cd and run ```
sudo grub-install /dev/sda
``` it might just do the trick.

---

### Post by nikhilk on 2009-07-29
> **frunns said:**
> This might not be the most awesome way to do it, but if you boot up the live cd and run ```
sudo grub-install /dev/sda
``` it might just do the trick.

A simpler way to attempt correcting your menu.lst is to run```
sudo update-grub
```

---

### Post by frunns on 2009-07-29
Oh, didn't know about that. :) Sounds better.

---

### Post by Cope57 on 2009-07-29
Look in /boot/grub/menu.lst~

When changes are made, you will find files with the tilde "~" attached to the filename, depending on the program that created the file. Even if you did not create a menu.list.bak, there is a good chance that there is a menu.lst~ in the /boot/grub/ directory which you could use as a backup. The ~ designates a tilde delimited file which will get erased eventually during cleanup and logrotate, or whatever... ;)

---

### Post by Cfhs_1 on 2009-07-29
Sudo update-grub


I thought that would work, but I ran it from the live CD rebooted, and nothing changed... I'm going to look for that backup cope57 mentioned, I'll give the result when I get back.:D

---

### Post by Cfhs_1 on 2009-07-29
Backup of my menu.1st is not present. sudo update-grub tells me that it can't find a grub directory, I need to point specifically to my Ubuntu partition, how can I figure out witch partition it is though? I thinks it's hda(0,4) but that came back with the same error...

---

### Post by nikhilk on 2009-07-29
> **Cfhs_1 said:**
> Backup of my menu.1st is not present. sudo update-grub tells me that it can't find a grub directory, I need to point specifically to my Ubuntu partition, how can I figure out witch partition it is though?

Post the output of
```
sudo fdisk -l
```

That will provide the needed information to identify your Ubuntu partitions.

---

### Post by Cfhs_1 on 2009-07-29
I think I got it guys, I used Gparted to tell me witch partition it was (sda5) then I typed Sudo update-grub /dev/sda5 and it found the /boot/grub folder, then asked if I wanted it to rewrite Menu.1st and thats it. I'm about to go test it now. I'll give results. :popcorn:

---

### Post by Cfhs_1 on 2009-07-29
I thought I had it. I can Get The grub-update command to run, but it doesn't rewrite the file. as far as I can tell It does nothing At All to it.

---

### Post by nikhilk on 2009-07-29
> **Cfhs_1 said:**
> I thought I had it. I can Get The grub-update command to run, but it doesn't rewrite the file. as far as I can tell It does nothing At All to it.

Try adding the entry directly into the menu.lst file. Just need the output of fdisk command I mentioned earlier to identify the correct partition.

---

### Post by Cfhs_1 on 2009-07-29
I gave up guys, sorry. I just did a fresh install. Thanks for all your help though! :popcorn:

---

### Post by W4l0ck on 2009-07-29
Nothin I can do, but how do you like win7?
 
I had it when it was in alpha last year.

---

### Post by JKyleOKC on 2009-07-29
If you still want to accomplish your original goal of eliminating the recovery entries and memtest86, here's how to do it on your new menu.lst. Find these two areas (they are not adjacent to each other):
```
## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true
```and change them to read:
```
## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=false

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=false
```Save the changes, then run "sudo update-grub" again to rewrite the file.

It's not a great idea to eliminate the recovery option, though, since it might be the only way to get out of trouble without having to re-install one more time.

---

