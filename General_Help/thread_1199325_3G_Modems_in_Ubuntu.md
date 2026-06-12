---
title: "3G Modems in Ubuntu"
date: 2009-06-28
forum: General Help
---

### Post by Marcelo Santos on 2009-06-28
Hello people,

I'm getting mad to make an HSPDA modem to work... I'm using usb_modeswitch, and appears 4 serial ports in /dev/ (ttyUSB0, ttyUSB1, ttyUSB2 and ttyUSB4).

Sometimes the USB1 works and connect, and when I plug the dongle again, the wvdial doesn't work anymore, and I need to discover the correct USB port beetwen the 4 ports that appears in the system. Not always the same port that work before work after I plug the modem and another USB device.

Sometimes the correct USB port connects, but the network manager won't understand that situation and every application that depends on internet doesn't work anymore (ie: I CAN ping a internet ip address but, network manager says that I'm disconnected and firefox and others gnome applications doesn't work anymore).

Will at some point Ubuntu team or linux kernel team improve the support on this kind of device?

I just need it to finally switch to Ubuntu on my Acer Notebook.

Any help is welcome!

---

### Post by Steelmourne on 2009-06-28
An HSDPA via USB could be configured via Network Manager under "Mobile Broadband".

---

### Post by Marcelo Santos on 2009-06-29
Is not that simple: when I plug the dongle, the modem works in storage mode. Then, I need to switch it to MODEM mode. 

Ok, I do that and Network Manager do not recognize the device, and in this case I need to use wvdial to dial and connect to internet.

So far, so good... But the network manager don't recognize the active 3G connection, and informs that I don't have any connection and cannot surf on internet... Firefox and any internet dependent application stop to work.

I replaced the network manager with wicd and in this case I lose the VPN wizards, falling back to text interface (for me: no problem with that.)

My only complain is in a near future, the Ubuntu work with these devices without so much pain.

Thanks!

---

### Post by 3rdalbum on 2009-06-29
> **Marcelo Santos said:**
> My only complain is in a near future, the Ubuntu work with these devices without so much pain.

This will probably happen. You used to have to use USB Modeswitch on the Huawei E160 modems, until the modeswitching became part of the driver. Your modem will probably automatically modeswitch on a later version of Ubuntu.

Unfortunately, the whole "virtual drivers CD" feature of these new USB devices is implemented differently every time; there's nothing standard about them, which means that the system has to be reverse-engineered with usb_modeswitch for every new device driver.

---

