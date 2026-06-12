---
title: "Grub: &quot;Error 11: Unrecognized device string&quot; when booting"
date: 2009-07-30
forum: General Help
---

### Post by subreyfer on 2009-07-30
Hi, I'm an Ubuntu newbie running 9.04 on my laptop. A few hours after doing a "partial upgrade" yesterday, my mouse pointer stopped responding, so I restarted the computer. However, since then, I've been unable to boot from the hard drive at all.
 
 After loading the Grub menu, it tells me
 > Error 11: Unrecognized device string
 
 Press any key to continue... and then sends me to this list:
 > Debian GNU/Linux, kernel 2.6.28-14-generic
 Debian GNU/Linux, kernel 2.6.28-14-generic (recovery mode)
 Debian GNU/Linux, kernel 2.6.28-13-generic
 Debian GNU/Linux, kernel 2.6.28-13-generic (recovery mode)
 Debian GNU/Linux, kernel 2.6.28-11-generic
 Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
 Debian GNU/Linux, kernel memtest86+ I'm pretty sure something is wrong here because I'm on Ubuntu, not Debian. Trying to boot any of these names by pressing Enter only gives me the same Error 11 and returns me to this list, making booting impossible. (I'm having to post this from a borrowed computer.)
 
 The first thing I tried was to Google the error message, but most of the results I found were people who had accidentally removed or broken Grub by installing multiple OSes. I've never even tried to dual boot or partition this computer, so I don't know how that could happen unless yesterday's update did it.
 
 I've also tried booting from a live CD, reinstalling Grub and restarting without the CD, but nothing changed.

If this problem can be solved without having to reinstall Ubuntu completely, help would be greatly appreciated! I can provide more information if somebody walks me through it.

---

### Post by marcopalla on 2009-07-30
should be usefull boot from disk and paste here the content of

/boot/grub/menu.lst

---

### Post by subreyfer on 2009-07-30
> **marcopalla said:**
> should be usefull boot from disk and paste here the content of

/boot/grub/menu.lst
Sorry to be clueless, but how do I open that? If you mean booting from the hard drive, the problem is, it's not letting me.

When I boot from the live CD and try "gksudo gedit /boot/grub/menu.lst", I get a blank page, which I guess means it doesn't exist.

---

### Post by marcopalla on 2009-07-30
sorry, I mean from a bootable CD,

in that case the root directory is on the cd itself? I'm not shure and not a guru,
if so previously you have to know on witch disk partition to look:

fdisk -l

then look for the /boot directory and the menu.lst file
menu.lst file is the file Grub use to give you the list, I think the problem is there.

EDIT: from grub gnu manual

11 : Unrecognized device string This error is returned if a device string was expected, and the string encountered didn't fit the syntax/rules listed in the [Filesystem]("http://www.gnu.org/software/grub/manual/grub.html#Filesystem").

---

### Post by subreyfer on 2009-07-30
Well, I managed to at least boot properly after seeing your link to the Grub manual. I think I can work out the rest. Thanks very much for the help!

(The text after "root" was a long stream of numbers and letters, but when I replaced it with "(hd0,0)" it worked.)

---

### Post by marcopalla on 2009-07-30
you are welcome :D

---

### Post by Ezure on 2009-10-28
> **subreyfer said:**
> Well, I managed to at least boot properly after seeing your link to the Grub manual. I think I can work out the rest. Thanks very much for the help!

(The text after "root" was a long stream of numbers and letters, but when I replaced it with "(hd0,0)" it worked.)

I have the same issue. In a wave of stupidity, I installed the old GFXboot onto my work laptop and after an update I was presented with this exact same error. I also tried replacing the UUID with (hd0,5) (my partition) and it almost worked.

Now I get dropped out of the boot process at a "(initramfs)" prompt with the following text:

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/************************ does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu *****)
Enter 'help' for a list of built-in commands

--------------
I'm going to try to do what I can, but if anyone knows any solutions please share. It looks like there is something else pointing to the UUID instead of the partition #.

And if you would be so kind to direct me how to get rid of gfxboot and go back to regular Grub(2?) safely I'd be very grateful. 

As it has already been said in this thread, this specific problem is hard to find details about.

-----------

Ok, so I mounted my drive, changed my menu.lst from the UUID to the partition, mounted proc and dev, chroot 'ed, did a grub-install hd0,5 and (this could be where I went bad) update-initramfs -u .

Unfortunately now after the boot menu, I am presented with a black screen and a still underscore-like cursor in the top-left, and a flashing caps-lock light.

I have an identical laptop which I will now be attempting to copy the boot folder from.

----------------

Error 15

I tried fixing the UUID in menu.lst and fstab, and updated initramfs but it took me right back to the black screen.

I think I'm doing more harm than good here. Are there files located somewhere else related to grub? It seems that the same peculiarities are present, characteristics of GFXboot.

I think it could be rescued by tar ing my partition but excluding the areas where the problem lies, then reinstall from livecd, followed by un tar ing my archive back onto the partition. Can anyone share some insight as to which folders/files I need to exlude to make this work?

------------------------

Standback!

It's all done. I booted from LiveCD, then mounted my partition, opened a terminal

mount -o bind /dev /media/disk/dev
mount -o bind /proc /media/disk/proc
chroot /media/disk
aptitude

I searched for GFXboot and then uninstalled it.
I then had to install the driver to get my network card working.
From a separate terminal window I ran

sudo apt-get install -d grub-pc

That downloaded 2 packages, Grub-pc***** and lib*****, but I still needed to get os-prober. So ...

I went back into my chroot'ed terminal window, ran aptitude again, searched for os-prober and tried to download it but it failed. However, it tells you from where it failed to download, which I promptly typed into a firefox address bar and download the file I needed.

Then I grabbed it and the other two from /var/cache/apt, put them into the /media/disk/var/cache/apt**** folder and then went back to my aptitude window.

From there I chose to install os-prober which installed grub-pc and the lib one as well and then after a few prompts, I rebooted and SHAZAAAAAMMMMM!!!!!!!!!!

If you couldn't tell, I'm pretty stoked.

Thank all. I hope this helps someone in the future, or at minimum, helps *me *out when I managed to kill my grub MBR again.

Peace!

---

### Post by creechal on 2010-03-25
I am running Karmic on my computer. I just upgraded the kernel (2.6.31-20-generic) When I rebooted the computer it would not boot in the 2.6.31-20 kernel. It would hang on the splash screen. 

I booted into the 2.6.31-19 kernel. I found some suggestions to update the grub. So I updated grub through the terminal. It made a change to the menu.lst (I think that is the file). 

I rebooted again. This time it does not matter which kernel I use. I get the same error. "Error 11: unrecognized device string"

I have a Januty Live CD. I brought that up, choose use, without installing. It starts up and then the system shuts down. 

I am not sure what to do next. On the plus side. I backed up my computer before messing with grub. So a re-install is a possibility. Can I fix it without that?

Thanks for the help.

---

### Post by acreech on 2010-03-25
> **creechal said:**
> I am running Karmic on my computer. I just upgraded the kernel (2.6.31-20-generic) When I rebooted the computer it would not boot in the 2.6.31-20 kernel. It would hang on the splash screen. 

I booted into the 2.6.31-19 kernel. I found some suggestions to update the grub. So I updated grub through the terminal. It made a change to the menu.lst (I think that is the file). 

I rebooted again. This time it does not matter which kernel I use. I get the same error. "Error 11: unrecognized device string"

I have a Januty Live CD. I brought that up, choose use, without installing. It starts up and then the system shuts down. 

I am not sure what to do next. On the plus side. I backed up my computer before messing with grub. So a re-install is a possibility. Can I fix it without that?

Thanks for the help.

I posted that with my sons account. So I have got my computer running on a live cd now. Can I fix this error through the terminal while I am on a live cd?

it seems that my problems started with the kernel update and then got worse with the grub update. 


thanks 

acreech

---

### Post by acreech on 2010-03-25
This is the content of my /boot/grub/menu.lst

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
# kopt=root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=71199ba9-de22-4254-b6e9-134a6751421e

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
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.31-20-generic
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro quiet splash
initrd		/boot/initrd.img-2.6.31-20-generic

title		Debian GNU/Linux, kernel 2.6.31-20-generic (recovery mode)
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Debian GNU/Linux, kernel 2.6.31-19-generic
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro quiet splash
initrd		/boot/initrd.img-2.6.31-19-generic

title		Debian GNU/Linux, kernel 2.6.31-19-generic (recovery mode)
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Debian GNU/Linux, kernel 2.6.31-17-generic
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro quiet splash
initrd		/boot/initrd.img-2.6.31-17-generic

title		Debian GNU/Linux, kernel 2.6.31-17-generic (recovery mode)
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Debian GNU/Linux, kernel 2.6.31-16-generic
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro quiet splash
initrd		/boot/initrd.img-2.6.31-16-generic

title		Debian GNU/Linux, kernel 2.6.31-16-generic (recovery mode)
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Debian GNU/Linux, kernel 2.6.31-15-generic
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro quiet splash
initrd		/boot/initrd.img-2.6.31-15-generic

title		Debian GNU/Linux, kernel 2.6.31-15-generic (recovery mode)
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Debian GNU/Linux, kernel 2.6.31-14-generic
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro quiet splash
initrd		/boot/initrd.img-2.6.31-14-generic

title		Debian GNU/Linux, kernel 2.6.31-14-generic (recovery mode)
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Debian GNU/Linux, kernel 2.6.28-16-generic
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro quiet splash
initrd		/boot/initrd.img-2.6.28-16-generic

title		Debian GNU/Linux, kernel 2.6.28-16-generic (recovery mode)
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=71199ba9-de22-4254-b6e9-134a6751421e ro single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Debian GNU/Linux, kernel memtest86+
root		71199ba9-de22-4254-b6e9-134a6751421e
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=05502dba-1d9d-41b7-ad03-ecf67e855e16 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=05502dba-1d9d-41b7-ad03-ecf67e855e16 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=05502dba-1d9d-41b7-ad03-ecf67e855e16 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=05502dba-1d9d-41b7-ad03-ecf67e855e16 ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05502dba-1d9d-41b7-ad03-ecf67e855e16 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05502dba-1d9d-41b7-ad03-ecf67e855e16 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by Bro3 on 2011-03-29
Changing "root" to "uuid", e.g. 
root        71199ba9-de22-4254-b6e9-134a6751421e
to 
uuid        71199ba9-de22-4254-b6e9-134a6751421e

solves the problem for me. Unfortunately the changes are reverted on every kernel update.

---

