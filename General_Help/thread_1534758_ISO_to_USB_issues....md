---
title: "ISO to USB issues..."
date: 2010-07-20
forum: General Help
---

### Post by Selim873 on 2010-07-20
Hi everybody! I've been an Ubuntu user for a while and I found it difficult to just have Ubuntu as the only OS on my netbook, I have a Windows XP SP3 disk and I wanted to wipe out my current partition, install XP, then reinstall Ubuntu as a dual boot, but I can't find any way to easily convert a Windows XP SP3 ISO to USB... The ISO is about 600 or so MB, I'm using a 2GB USB key... WintoFlash is very incompatible with Wine, and Startup Disk Creator won't accept my Windows ISO, but I think SDC is only compatible with Linux ISOs.

Any ideas?  :-k

EDIT: Okay, I found a program called UNetBootin, I'll let you guys know how it works out. If you know anything though, don't hesitate to post it incase it fails!  :P

EDIT2: It failed... I got something like this on my screen, I'll use a quote bar to pretend to be by screen.

> 
boot:_




After that, anything could be typed in, like a terminal, but I hit enter when it was blank, then I got a loader type screen with a box that had "Default" highlighted, when I hit enter on that, the automatic boot timer would reset... So I just restarted my netbook then formatted my USB stick...


EDIT3: I'll just use a virtual machine.  But if there is ANYONE who was where I was at, maybe answers could still be posted? ;)

---

### Post by C.S.Cameron on 2010-07-20
I understand this will put the Windows 7 install disk on USB:

1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
-> put bootable flag (right click in gparted - manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick.

From Amedac

---

### Post by Selim873 on 2010-11-25
How did I miss that?!  I'll give it a shot!

---

### Post by oldfred on 2010-11-26
Some more links if the above does not work.

Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
Windows In Your Pocket USB using BartPE
[http://www.tomshardware.com/reviews/windows-pocket,1113.html](http://www.tomshardware.com/reviews/windows-pocket,1113.html)

---

### Post by Selim873 on 2010-11-26
I'm currently looking at the first link that you gave me, at this time, neither of my USB keys worked with C.S.Cameron's suggestion.  I'm using an Aspire One and I'm trying a Sandisk Cruzer which is listed in the first link.  On C.S.Cameron's idea, the Cruzer gave me an error saying "Error loading Operating System_" and on my old 2GB (what I installed Ubuntu with) just did nothing... it's light never blinked or anything, trying one of the links that oldfred handed to me.  I also know that this XP iso works because I copied my own Disc to an ISO, then used a USB drive to put it on my netbook, I was able to install XP on VirtualBox with it, so it's not corrupted.

---

### Post by C.S.Cameron on 2010-11-26
I can also confirm that my above post only works with Windows Seven and not XP

---

### Post by Selim873 on 2010-11-26
Oh ok, if I can't get XP to work out, I'll get a 7 disc from somewhere and try your suggestion again.

EDIT: I do agree though that the XP installer is VERY picky, I'll go ahead and try this.  I got a 7 disc lying around anyway.  Why not try it...

---

