---
title: "Live USB"
date: 2012-06-15
forum: General Help
---

### Post by DFergLSI on 2012-06-15
I am trying to make a live USB.  I found some directions on using Startup Disk Creator.  Problem is it doesn't see the USB stick.
 
Now I go to GParted - Check USB stick is there and is formated ext4.
 
got to the home folder - Check USB stick is there and accessable.
 
gotto "Create Startup Disk" it see the Ubuntu CD I have in the drive but will not see the usb stick that every other problem in Ubuntu sees.

---

### Post by Rex Bouwense on 2012-06-15
What is the make and size of the flash drive that you are trying to use?  have you tried another flash drive?

---

### Post by wilee-nilee on 2012-06-15
> **DFergLSI said:**
> I am trying to make a live USB.  I found some directions on using Startup Disk Creator.  Problem is it doesn't see the USB stick.
 
Now I go to GParted - Check USB stick is there and is formated ext4.
 
got to the home folder - Check USB stick is there and accessable.
 
gotto "Create Startup Disk" it see the Ubuntu CD I have in the drive but will not see the usb stick that every other problem in Ubuntu sees.

The usb has to be a fat partiton. A full install would be a ext type.

---

### Post by DFergLSI on 2012-06-15
Ok, I can boot from the UDB now.  But each time I boot it comes up with the "Try Ubuntu" or "Install"  I would like to go straight to the desktop.

---

### Post by wilee-nilee on 2012-06-15
> **DFergLSI said:**
> Ok, I can boot from the UDB now.  But each time  I boot it comes up with the "Try Ubuntu" or "Install"  I would like to  go straight to the desktop.

You would need a full install for that.

The Startup Disk Creator, just loads the ISO; with a persistent file if you choose that.

Although loading the usb with unetbootin, or the multisytem loader at pendrive linux, will give you the illusion of a desktop boot. Both have persistent options as well

---

### Post by DFergLSI on 2012-06-15
> **wilee-nilee said:**
> You would need a full install for that.
 
The Startup Disk Creator, just loads the ISO; with a persistent file if you choose that.
 
Although loading the usb with unetbootin, or the multisytem loader at pendrive linux, will give you the illusion of a desktop boot. Both have persistent options as well
 
 
ARGGG!!  That is what I wanted to do.  But no matter where I looked I could not get it to install to the USB from the installer.  Oh, well back to Haiku.

---

### Post by Rex Bouwense on 2012-06-15
Look here.
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
It talks about installing Lubuntu but I imagine Ubuntu would work as well.

---

