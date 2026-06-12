---
title: "Wubi installer error"
date: 2010-10-29
forum: General Help
---

### Post by Hybridgreen on 2010-10-29
Hey guys, i use a HP Pavilion dv6-3016. I use windows 7 64-bit. I was using Wubi installer to download and to install Ubuntu 10.04. An error message comes up stating the following:
 
An error occurred:
 
Premission denied
 
For more information, please see the log file:
c:\users\(myname)\appdata\local\temp\wubi\-10.04.1-rev190.log
 
I really want to use Ubuntu as it is my prefered OS to windows, thanks for the help in advance, 
Hybridgreen.

---

### Post by cpmman on 2010-10-29
Wubi is really for trying ubuntu on your machine, not for long-term installations.  It would be better to download the normal live cd and install ubuntu as a dual boot with Windows 7.  I went from a wubi install on a CQ61 to a dual boot and whilst it worked for me eventually, I would not recommend anyone to do that.

---

### Post by Hybridgreen on 2010-10-29
thanks for the answer however, i am only interested downloading over wubi.

---

### Post by jokes_finder on 2010-10-29
I did install Ubuntu using wubi on my laptop ( Toshiba Satellite L650-10M x64 bit ) and no error occurred..

---

### Post by Hybridgreen on 2010-10-29
Yes, but your not using a HP computer and also your probably not using a 64-bit AMD win 7 system

---

### Post by philinux on 2010-10-29
> **Hybridgreen said:**
> thanks for the answer however, i am only interested downloading over wubi.

There is also a problem with wubi when a grub update takes place. It nukes the windows bootloader so you end up with having to reinstall the bootloader to access windows.

I would recommend you try either the live usb or live cd. Then install as a dual boot.

---

### Post by Hybridgreen on 2010-10-29
Okay, is there anywhy to delete this partition if Ubuntu did not work on my system, FN/shortcut keys i'm talking.

---

### Post by cpmman on 2010-10-29
Either the uninstall.exe provided with wubi or W7's own remove programme will do it.

---

### Post by Hybridgreen on 2010-10-29
If i download ubuntu can i make a live usb with windows so i can trail it and see if it works?

---

### Post by cpmman on 2010-10-29
Yes - that is what the live cd/usb is for.

---

### Post by Hybridgreen on 2010-10-29
> **cpmman said:**
> Yes - that is what the live cd/usb is for.
 
you must think i'm an idoit, i know that there is a live cd you can download. However how do i make a live usb?

---

### Post by cpmman on 2010-10-29
Sorry if I gave that impression - it is difficult to know what level of experience to address.

The usb live [***_https://help.ubuntu.com/community/Installation/FromUSBStick_***]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by Verbeck on 2010-10-29
to create a live usb from windows
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
if you scroll down a bit, you'll see sreenshots

[]("https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows")

---

