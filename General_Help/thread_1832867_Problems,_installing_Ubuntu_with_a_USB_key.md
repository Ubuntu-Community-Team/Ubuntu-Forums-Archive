---
title: "Problems, installing Ubuntu with a USB key"
date: 2011-08-25
forum: General Help
---

### Post by LorteMidget on 2011-08-25
Hi, I'm trying to install Ubuntu 11.04 to my netbook. Therefore, I use my USB key, since i do not have a CD drive. 

But when I try to boot my computer from the USB key, where my Ubuntu setup files is stored on, i get this message:

"SYSLINUX 3.82 2009-06-09 EBIOS COPYRIGHT (C) 1994-2009 H. Peter Anvin et al"

The only thing I can do from here, is to turn of my computer. 

Hope you guys can help!

---

### Post by seawolf167 on 2011-08-25
Did you make a bootable USB drive with something like [UNetbootin]("http://unetbootin.sourceforge.net/")? Is your BIOS set properly to allow booting from that USB drive?

---

### Post by LorteMidget on 2011-08-25
I downloaded the Ubuntu ISO file from their website, burned it to a CD, and on the CD, there was this "usb-creator" program, which i used. I don't know about my BIOS, how it'set..

---

### Post by Topsiho on 2011-08-25
If you have managed to use your liveCD, then your BIOS is set so the computer boots from the CD-Rom first, before trying to boot from something else such as the hard disk.

On modern computers you can often boot from USB, and choose to do so by pressing F12 (or so), when booting. Or you change the BIOS so that the computer boots from USB first, and then (if there is no bootable USB-stick) from hard disk or CD-ROM.

Topsiho

---

### Post by seawolf167 on 2011-08-25
Ensure that USB booting is set as per the above post - I've never tried the "usb-creator" program so I can't comment on that, but one that has worked for me every time was the one I previously linked, UNetbootin, if you still can't get it booting off the USB, try that program and see if it works for you.

---

### Post by nothingspecial on 2011-08-25
> **seawolf167 said:**
> Ensure that USB booting is set as per the above post - I've never tried the "usb-creator" program so I can't comment on that, but one that has worked for me every time was the one I previously linked, UNetbootin, if you still can't get it booting off the USB, try that program and see if it works for you.

+1

usb-creator failed for me yesterday but unetbootin worked for the same iso. You can install it from the software centre

---

### Post by LorteMidget on 2011-08-25
Ill try Unetbootin, thank you, hope it works!

---

### Post by e79 on 2011-08-25
Have you tried with the Universal USB Installer from pendrivelinux.com ?

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by LorteMidget on 2011-08-25
Thank you very much!! UNnetbootin works, and Ubuntu is now installing! :)

---

### Post by seawolf167 on 2011-08-25
Awesome, glad you are up and [or soon to be] running! Please mark this thread as solved under "Thread Tools" -> "Mark as Solved".

---

