---
title: "Need help with Lenovo IR receiver and Ubuntu 12.04 (LIRC)?"
date: 2012-07-16
forum: General Help
---

### Post by BigB42078 on 2012-07-16
I bought this receiver off ebay and can't get it to work. It receives ir signals, lights up when pressing buttons, but nothing in XBMC. I used these settings suggested on another site.

&#8220;Windows Media Center Transceivers/Remotes (all)&#8221; 

&#8220;Microsoft Windows Media Center V2 (usb) : Direct TV Receiver&#8221;



 Also tested in Windows 7 and it works perfectly with Media Centre.

**It shows this in Windows 7:**

Keyboards:
Microsoft eHome MCIR 109 Keyboard
Microsoft eHome MCIR Keyboard
Microsoft eHome Remote Control Keyboard keys


Universal Serial Bus controllers:
Microsoft eHome Remote Control Keyboard keys

---

### Post by CharlesA on 2012-07-17
Try a Windows forum --> [http://www.sevenforums.com/](http://www.sevenforums.com/)

EDIT: Actually, if it is a problem with Ubuntu not detected it, you could always run something like:

```
lsusb
``` with the device plugged in.

---

### Post by BigB42078 on 2012-07-17
I don't need help with MS Windows 7, it works just fine I just figured it might help identify what kind of IR receiver it is.

I tried lsusb and looks like it's recognized as:
Bus 009 Device 003:  ID 0609:0357 SMK Manufacturing, Inc.
Bus 009 Device 004:  ID 17ef:602b Lenovo

I also have the Lenovo N5902 Multimedia Remote with keyboard but I believe it is this one:
Bus 004 Device 002:  ID 04d9:0022 Holtek Semiconductor, Inc. Portable Keyboard

How do I get it to control programs with a MCE RC6 remote?:popcorn:

---

### Post by BigB42078 on 2012-08-05
I have this receiver working now thanks to the help of  XBMC forum. The vendor/product-id isn't recognized

I disconnected the device and used these commands with root to recognize it:

[B]rmmod mceusb
modprobe mceusb
echo 0609 0357 > /sys/bus/usb/drivers/mceusb/new_id[/B]

reconnected it and used **dmesg** to see if device was recognized

Everything works out of box now, with the previous settings. Using my "One For All" "OARI06G" with Media Center PC code in XBMC Eden. :guitar:

---

