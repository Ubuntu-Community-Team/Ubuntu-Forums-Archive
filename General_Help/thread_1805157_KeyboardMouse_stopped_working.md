---
title: "Keyboard/Mouse stopped working"
date: 2011-07-15
forum: General Help
---

### Post by Tuskator on 2011-07-15
I have an Acer 5102 WLMi laptop from 2005 with Ubuntu 9.10 installed. It has worked fine for years but now when I boot up my mouse and keyboard don't respond leaving me stuck at the login screen. I have tried using a USB mouse without sucess. My USB-powered cooling fan still works in all three USB ports fine. I have tried booting into the LiveCD and gotten the same results except for the CD auto-logging in. Eht0 still auto-connects to the network fine in the LiveCD. I can't find any wrong except for the keyboard and mouse not responding. My next step is to burn a LiveCD with start-up scripts to enable ssh. Can someone please help?

EDIT: Also the touch-pad doesn't respond either

---

### Post by Tuskator on 2011-07-16
Anyone??

---

### Post by DawieS on 2011-07-16
If your keyboard and mouse also do not respond with the Live CD (as it did when you originally installed Ubuntu), then you probably have a hardware problem now (unless the BIOS settings was changed in the meantime). Thus it would not help to burn another Live CD.

Does the keyboard work when booting? Can you press a key and get into the BIOS? If not, then you have a hardware problem (unless there is some button that would reset your BIOS to fail-safe settings).

---

### Post by LowSky on 2011-07-16
It does sound like a hardware issue. Just so you understand better, USB ports can have multiple functions. Most can provide power as a secondary function. If the port is not recieving a signal from the input device it could mean a problem with the motherboard, maybe the usb control chip. which is not fixable in 99.9999% of all cases. 

like the last poster said it could be a very odd software glitch, and you can try using the keyboard to enter BIOS as a test.

---

### Post by Tuskator on 2011-07-18
I was afraid of it being a hardware problem.

No, the keyboard is unresponsive during boot and can't load the BIOS.

Thanks anyway.


One thing I think is weird is that the Ethernet port still connects and gets an IP address from DHCP fine and the CD/DVD works fine too. Could this be because the mouse/keyboard/touch-pad are USB and only USB isn't working, while the CD/DVD drive and Ethernet port aren't?

Anyone know how to take apart a Acer 5102 WLMi? I googled some but couldn't find anything. All I can get off is the panels for the hard drive, fan, and RAM.

---

