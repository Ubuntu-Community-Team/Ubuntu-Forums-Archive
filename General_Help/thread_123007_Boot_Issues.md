---
title: "Boot Issues"
date: 2006-01-29
forum: General Help
---

### Post by thepocketdrummer on 2006-01-29
The program that Kubuntu installs to select which OS to boot from seems to be having issues.

When I updated Kubuntu, I have Kubuntu with a -9 and -10 next to it, the same thing with Default next to it, and the same with with recovery next to it. I have 8 Kubuntu entries on this thing!

First, I'd like to remove all the old -9 Kubuntus so the -10 (recent) ones only show up.

Second, I'd like to make Windows the Default.

Does anyone know how to do that?

---

### Post by obibok on 2006-01-29
This is normal behaviour. Nothing wrong with that :D Your system will keep older kernel versions unless you tell it to remove them.

Use Adept or Synaptic (or your favourite package management tool) to remove the older versions if you like.

To change the default boot options, you'll need to edit **/boot/grub/menu.lst** or **/etc/lilo.conf** (which one do you use?). Look for "*default*". Or just post your file here and some good folks may show you which lines to edit.

---

### Post by thepocketdrummer on 2006-01-29
I use Grub and Adept.

How would I go about changing those files so only the necessary ones show up? I'm feel like a beginner to computers all over again. I'm pretty savvy in Windows, but I guess thats not really saying much, lol.

---

### Post by thepocketdrummer on 2006-01-29
Do I just search for the old version number in Adept and delete the packages?

---

### Post by thepocketdrummer on 2006-01-29
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous 
root		(hd0,1)
kernel		/boot/vmlinuz.old root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz.old root=/dev/hda2 ro single
initrd		/boot/initrd.img.old
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by thepocketdrummer on 2006-01-29
... those smileys aren't supposed to be there.

---

### Post by obibok on 2006-01-29
In Adept, search for *2.6.12* [X] installed and just remove *linux-image-2.6.12-9-xxx* and *linux-restricted-modules-2.6.12-9-xxx* (xxx being your architecture = i386, 686 or k7). Be careful not to remove the most recent kernel image, so doublecheck before commiting changes! This should actually remove the kernel entry from GRUB for you but I'm not sure.

To change the default boot option in GRUB, edit */boot/grub/menu.lst*.

Find:
```
default 0
```

and change it to:

```
default saved
```

Then, add in the OS section (example from GRUB used here):

```
title         Windows 95/98/NT/2000
root          (hd0,0)
makeactive
chainloader   +1
**savedefault**
```

---

### Post by obibok on 2006-01-29
OK, so change the **default** from **0** to **saved** (top of the file) and then you can just clean up your OS menu like that:

```
## ## End Default Options ##

title Ubuntu, kernel 2.6.12-10-amd64-generic
root (hd0,1)
kernel /boot/vmlinuz root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img
boot

title Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz root=/dev/hda2 ro single
initrd /boot/initrd.img
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```

---

### Post by thepocketdrummer on 2006-01-29
Could I just copy that and paste it in? Where is that Default 0 part? Should I remove the savedefault from the other two and put it under Windows?

I'm stupid when it comes to linux #-o

---

### Post by thepocketdrummer on 2006-01-29
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


That's what it looks like now.

---

### Post by obibok on 2006-01-30
```
[SIZE="1"]# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## ## End Default Options ##

title Ubuntu, kernel 2.6.12-10-amd64-generic
root (hd0,1)
kernel /boot/vmlinuz root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img
boot

title Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz root=/dev/hda2 ro single
initrd /boot/initrd.img
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1[/SIZE]
```

---

### Post by thepocketdrummer on 2006-01-30
Ok, new problem. I tried to save it and got this message.

> The document could not be saved, as it was not possible to write to file:///boot/grub/menu.lst.
Check that you have write access to this file or that enough disk space is available.


How do I write to this file?

---

### Post by thepocketdrummer on 2006-01-30
oh, and are all the changes you made after

## ## End Default Options ##

or is there something above it that needs to be changed too?

---

### Post by thepocketdrummer on 2006-01-30
ok, I figured out

```
sudo gedit /boot/grub/menu.lst
```

and I copied and pasted what you wrote into it. I'll restart and see if it fixed it.

---

### Post by thepocketdrummer on 2006-01-31
Kubuntu is still the Default :cry: 

Anyone know how to fix it?

---

### Post by obibok on 2006-01-31
```
default saved
```
should remember your last boot option. So, once you boot Windows and reboot, GRUB should default to Windows again. But if you always want to have Windows preselected, then change line #12 to:

```
default 5
```

---

### Post by thepocketdrummer on 2006-01-31
Actually I restarted again and Windows was preselected already.

Thanks! :D

---

### Post by awalesminfo on 2006-03-18
default 9

change 0 to 9 it will set ur default boot option to windows;)  as ur having windows entry in 10 th field but as ur  setting default to 5 ? and still its working how ???

---

