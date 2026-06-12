---
title: "Changing Location of XP Option in Boot Loader Menu"
date: 2009-07-15
forum: General Help
---

### Post by Ubuntist on 2009-07-15
Using grub, I dual-boot Jaunty and XP, defaulting to Jaunty. In the grub menu, the standard Jaunty boot appears as the first option, followed by safe boot and memory test Jaunty options and then by the XP option.

I'd like to keep Jaunty as the default but have XP appear just above it in the boot loader menu, so that on those unfortunately still frequent occasions when I need XP I can select it with just one touch of an arrow key. Somehow I did this on a previous computer, but I can't figure out how to do it now. Could someone please enlighten me?

---

### Post by Java Geek on 2009-07-15
Check your /boot/grub/menu.lst file and open it up as root. Then rearrange the selections as necessary and look for the default option and select that to 0. good luck

---

### Post by theluddite on 2009-07-15
You know how to edit /boot/grub/menu.lst right?  Make sure you BACK IT UP first before you mess around with it!

---

### Post by jim_ryan on 2009-07-15
I used this tutorial to dual boot XP and ubuntu.  I'm an idiot and I got it working...

[http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")

oh, and I just commented out all the other Jaunty boot selections, and renamed the two selections I use.   


title		Ubuntu 9.04 Jaunty Jackalope 64
uuid		3b7a5306-39ed-4430-9fbc-44679fada010
kernel		/boot/vmlinuz-2.6.28-13-generic root=quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

#title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
#uuid		3b7a5306-39ed-4430-9fbc-44679fada010
#kernel		/boot/vmlinuz-2.6.28-13-generic root=ro  single
#initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		3b7a5306-39ed-4430-9fbc-44679fada010
#kernel		/boot/vmlinuz-2.6.28-11-generic root=0 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		3b7a5306-39ed-4430-9fbc-44679fada010
#kernel		/boot/vmlinuz-2.6.28-11-generic root=ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

#title		Ubuntu 9.04, memtest86+
#uuid		3b7a5306-39ed-4430-9fbc-44679fada010
#kernel		/boot/memtest86+.bin
#quiet

and added my XP potion above:
### BEGIN AUTOMAGIC KERNELS LIST

like so...

title		Superior Windows XP 64
 rootnoverify		(hd1,0)
 savedefault
 makeactive
 map			(hd0) (hd1)
 map			(hd1) (hd0)
 chainloader	+1

### BEGIN AUTOMAGIC KERNELS LIST

mine defaults to xp after 10 sec timeout though, im not sure how to switch that... again im an idiot.

---

### Post by theluddite on 2009-07-15
Change this accordingly in /boot/grub/menu.lst

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3



---

### Post by nikhilbhardwaj on 2009-07-15
do 
sudo apt-get install startupmanager
then sudo startupmanager

it allows you to graphically manage all that and more

---

### Post by ramnarayan on 2009-07-15
> **Ubuntist said:**
> 

I'd like to keep Jaunty as the default but have XP appear just above it 

carefully in a terminal
```
sudo gedit /boot/grub/menu.lst

```

cut and paste the set of entries related to windows just below the jaunty main entry

save and exit 

The reason to paste below the main jaunty entry is because what ever is the first in the menu becomes the default - and thats something we don't want "do we" ;-) 

**
to be on the safe side bakup your menu.lst (meaning copy it somewher safe) in case you need to have the original back sometime

---

