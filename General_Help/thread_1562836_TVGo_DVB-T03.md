---
title: "TVGo DVB-T03"
date: 2010-08-28
forum: General Help
---

### Post by Blisk on 2010-08-28
Did someone manage to install this digital TV adapter on ubuntu.
Because I can't make it to work.
MY TV said there is no DVB adapter.

---

### Post by fun.k. on 2010-09-24
I have the same problem on Ubuntu 10.04, however I've tried to install linux-firmware-nonfree package (should work out-of-the-box). dmesg | tail -f doesn't show any info on plug/unplugging device, /var/log/messages gives only this info:

[ 1211.504149] usb 1-1: new high speed USB device using ehci_hcd and address 11
[ 1211.647123] usb 1-1: configuration #1 chosen from 1 choice

That' all.


I've also tried the procedure I've found for Ubuntu 9.04 - to download firmware (version 4.95, can be found at [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/]("http://www.otit.fi/%7Ecrope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/")) and copy it to /lib/firmware (have to be root).

After all, it seems DVB stick is not recognized. I have two computers, both running Ubuntu Lucid Lynx, both with the same behavior. 

I've also tried it under Windows 7 (yes, I'm one of those who "need" them...) - tuner is detected, driver installed, software installed and running (if I could call it like this - it has fallen down after 2 minutes...), so it seems the tuner is OK.

Anybody any ideas? Thanks in advance.

---

### Post by fun.k. on 2010-09-24
I'm sorry, dmesg gives also the same info on plug/unplug the device as /var/log/messages, that's:

[ 3280.524247] usb 1-1: new high speed USB device using ehci_hcd and address 12
[ 3280.666909] usb 1-1: configuration #1 chosen from 1 choice

Sorry, my bad...

---

