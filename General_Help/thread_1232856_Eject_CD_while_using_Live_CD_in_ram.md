---
title: "Eject CD while using Live CD in ram?"
date: 2009-08-06
forum: General Help
---

### Post by ENB on 2009-08-06
I've loaded Ubuntu (latest Live CD), and would like to eject the disc while still using the OS in ram. I know it's possible to do so, as I've done this with other Live CDs.

The reason is my harddrive is blank, and I would like to download and burn other ISOs without installing a new OS JUST to do so. Thanks for the help!

---

### Post by lildigiman on 2009-08-06
So what exactly is your question? You seemed to have answered it yourself...

---

### Post by prshah on 2009-08-06
> **ENB said:**
> I've loaded Ubuntu (latest Live CD), and would like to eject the disc while still using the OS in ram. I know it's possible to do so, as I've done this with other Live CDs.

Unfortunately, you can't do this with the Ubuntu Live CD.

Puppy, Knoppix and many other "light" live CD distros allow the CD to be ejected when the OS has finished loading, but not Ubuntu.

I would suggest putting the Ubuntu ISO on a bootable usb pen/flash drive, and booting off that, leaving your CD drive free.

---

### Post by ENB on 2009-08-06
> **lildigiman said:**
> So what exactly is your question? You seemed to have answered it yourself...

My question is, how do I do this?

> **prshah said:**
> Unfortunately, you can't do this with the Ubuntu Live CD.

Puppy, Knoppix and many other "light" live CD distros allow the CD to be ejected when the OS has finished loading, but not Ubuntu.

I would suggest putting the Ubuntu ISO on a bootable usb pen/flash drive, and booting off that, leaving your CD drive free.

Ah, this answers my question. Thanks! How come though? I have more than enough ram. I could load two Ubuntu's in it. Is it difficult to implement?

---

### Post by ENB on 2009-08-06
Oh, and is there a way to force it out via the terminal?

---

### Post by prshah on 2009-08-06
> **ENB said:**
>  I have more than enough ram. I could load two Ubuntu's in it. Is it difficult to implement?

I assume not; but it is beyond my skill level to advise you. However, this could turn into an interesting weekend project...

---

### Post by Mike_IronFist on 2009-08-06
Rather than booting it off of a Live CD and wishing it could run in RAM, boot into the live CD itself, and go to "System-->Administration" and use the USB Startup Disk Creator to make a bootable USB pendrive. Once you've done so, you need only to boot the USB flash drive and you can burn isos, and do whatever.

Of course you need to press the right BIOS key to select the the USB drive at boot. Usually the key used to "Change Boot Order" (F9 on my Compaq PC) makes it so easy that you just have to pick the USB flash drive and it will boot from it.

---

### Post by jointsnjams on 2009-10-21
> **ENB said:**
> My question is, how do I do this?



Ah, this answers my question. Thanks! How come though? I have more than enough ram. I could load two Ubuntu's in it. Is it difficult to implement?
meanwhile in another part of town... 

grub4dos booting ubuntu iso
[http://www.boot-land.net/forums/index.php?act=Print&client=printer&f=71&t=8797](http://www.boot-land.net/forums/index.php?act=Print&client=printer&f=71&t=8797)

>  ##
# grub4dos menu.lst entry for ubuntu live iso 
title Ubuntu LiveCD
find --set-root /ubuntu-9.04-beta-desktop-i386.iso
map /ubuntu-9.04-beta-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/ubuntu-9.04-beta-desktop-i386.iso quiet splash --
initrd /casper/initrd.gz
#


see also 
     :Grub4dos Guide - Map Command~Booting from .ISO Images
[http://diddy.boot-land.net/grub4dos/files/map.htm#hd32](http://diddy.boot-land.net/grub4dos/files/map.htm#hd32)
     :grub4dos, .iso images and (hd32) or (0xFF) mapping
[http://www.boot-land.net/forums/index.php?showtopic=5041&st=20#](http://www.boot-land.net/forums/index.php?showtopic=5041&st=20#)
     :BOOTING USB2.0 FAST SPEED !!!! 
[http://www.boot-land.net/forums/index.php?act=Print&client=printer&f=71&t=8605](http://www.boot-land.net/forums/index.php?act=Print&client=printer&f=71&t=8605)


i just wanted to add  
it is posible to do!. 
as i found this thread while browsing using usbFlash + grub4dos + ubuntu ect
=]

---

