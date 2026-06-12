---
title: "ipod nano not mounting"
date: 2009-08-20
forum: General Help
---

### Post by aeron-x on 2009-08-20
I have an iPod nano 2nd generation that I'm having trouble connecting in jaunty. It's definitely not auto-mounting but at least lsusb reports it's connecting:
```
Bus 001 Device 005: ID 05ac:1260 Apple, Inc. iPod Nano 2.Gen
```dmsg doesn't give much when I plug in the device, only this:
```
[  564.664042] usb 1-4: new high speed USB device using ehci_hcd and address 4
[  564.828082] usb 1-4: configuration #1 chosen from 2 choices
```It doesn't say anything about the sda/sdc, etc. info most sites are talking about, but i tested using mount with all the visible mount-points and none gave any results.

I'd like to have this connected as soon as possible, any help?

---

