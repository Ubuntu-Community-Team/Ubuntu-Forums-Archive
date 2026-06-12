---
title: "usb-storage: waiting for device to settle before scanning - It never settles!"
date: 2009-11-11
forum: General Help
---

### Post by VMOS on 2009-11-11
Hallo, I recently did a fresh install of kubuntu 9.10 (not by choice) and this is the last thing on my list of things that working in 9.04 but are now busted.
Anyways, my little usb drive/mp3 player, it no work! lsusb detects it ok, I get this in dmesg | grep -i usb

[B][ 8435.234428] usb 3-1.4: new full speed USB device using ohci_hcd and address 35
[ 8435.346441] usb 3-1.4: not running at top speed; connect to a high speed hub
[ 8435.358508] usb 3-1.4: configuration #1 chosen from 1 choice
[ 8435.364538] scsi22 : SCSI emulation for USB Mass Storage devices
[ 8435.364605] usb-storage: device found at 35
[ 8435.364608] usb-storage: waiting for device to settle before scanning
[/B]

and that's where it stops. I've tried every port, plugging it in and out again, rebooting, logging out, backwards, upside down with my eyes closed. I tried my old 128mb drive and that works fine. If I unplug the thing, dmesg shows

[ 8900.174782] usb 3-1.4: USB disconnect, address 35

The drive works fine on xp and I haven't written anything or removed anything since it was working on 9.04

anyone any ideas?

---

### Post by VMOS on 2009-11-11
I logged out and logged back in to a gnome session, it works perfectly there, looks like a karmic bug maybe?

---

### Post by marcio123 on 2010-06-14
I don't know if I'm alone but I have exactly the same problem in 10.04 :/ 

Some pendrives doesn't work and dmesg stops at

waiting for device to settle before scanning

Before kernel update all pendrives did not work, now it is better but problem still exists

---

### Post by markofealing on 2010-09-18
I have exactly the same problem with an LG KM900 mobile,. Cant see on board SD card, before 10.04 no problem.

Just keep getting "usb-storage: waiting for device to settle before scanning"

---

