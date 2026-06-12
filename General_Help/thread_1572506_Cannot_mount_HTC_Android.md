---
title: "Cannot mount HTC Android"
date: 2010-09-11
forum: General Help
---

### Post by AlexH76 on 2010-09-11
Hi,
When I connect my HTC Desire (and select to connect it as a diskdrive) to ubuntu (10.04.1) dmesg shows that the system sees a new usb 

[INDENT]Direct-Access  HTC   Android Phone  0100 PQ: 0 ANSI: 2
Attached scsi generic sg3 type 0
[sdc] Attached SCSI removable disk[/INDENT]

However, I cannot mount the device. fdisk -l /dev/sdc returns nothing.

lsusb finds the correct attributes:

[INDENT]idVendor     0x0bb4 High Tech Computer Corp.
idProduct     0x0ff9
[/INDENT]

I edited /etc/udev/rules.d/S51-android.rules accordingly:
[INDENT]SUBSYSTEMS==”usb”, ATTRS{idVendor}==”0bb4&#8243;, ATTRS{idProduct}==”0ff9&#8243;, MODE=”0666&#8243;[/INDENT]

Restarted udev, even restarted the machine, still no luck. 
How can I mount the device?

---

### Post by AlexH76 on 2010-09-12
Turns out that, after selecting "diskdrive" as connection type (on the phone, after connecting it) you also have to hit the "done" button to actually activate this connection(type)

---

