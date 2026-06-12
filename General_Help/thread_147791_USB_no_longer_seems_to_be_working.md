---
title: "USB no longer seems to be working"
date: 2006-03-20
forum: General Help
---

### Post by inkieminstrel on 2006-03-20
Unfortunately I don't know when this started happening, but USB used to work on my machine a couple of months ago and now it doesn't.  Neither my joystick nor my usb drive seems to be recognized on any of the ports on my machine (front and back).  /dev/input/js0 never shows up for the joystick and none of the /dev/sd* devices is my thumb drive.

The output from dmesg seems to be fine for anything I search for:

~$ dmesg | grep USB
[4294674.138000] USB Universal Host Controller Interface driver v2.2
[4294674.138000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
[4294674.200000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294674.200000] hub 1-0:1.0: USB hub found
[4294674.203000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
[4294674.265000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294674.265000] hub 2-0:1.0: USB hub found
[4294674.268000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
[4294674.330000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294674.330000] hub 3-0:1.0: USB hub found
[4294674.352000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
[4294674.353000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294674.357000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294674.357000] hub 4-0:1.0: USB hub found


I'm out of ideas.  Thanks for your help.

---

### Post by encompass on 2006-03-20
Have you tried mounting your drive as root?  it may be your user nolonger has permission.  That happened to me... I fixed it by going into the users and groups program and making sure I had all the rights I needed.  Hope it helps, it would not be fun losing your usb.

---

### Post by inkieminstrel on 2006-03-20
The problem is I don't see any of the devices in /dev, so I don't think I can even attempt to mount a device I can't see.

---

