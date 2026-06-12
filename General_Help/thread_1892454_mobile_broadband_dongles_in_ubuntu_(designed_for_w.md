---
title: "mobile broadband dongles in ubuntu (designed for windows?)"
date: 2011-12-08
forum: General Help
---

### Post by qwertyjjj on 2011-12-08
Is it possible to get mobile broadband dongles to work with UBUNTU?
Most of them seem to be designed to work on Windows but essentially most of them should have a way to dial out from their connection settings but I guess it is the driver that might be the problem and or the company's connection software.

---

### Post by bouncingwilf on 2011-12-08
All the mobile broadband dongles I've tried work "out of the box" with at least lucid, maverick and natty. When you plug them into the PC, the CD component of the dongle (containing windows software) pops up on the desktop - Ignore this software - you neither want nor need this but "Eject" this cd (rt click eject), wait a few seconds and then go to the network manager applet and set up your connection.


Bouncingwilf

---

### Post by qwertyjjj on 2011-12-08
> **bouncingwilf said:**
> All the mobile broadband dongles I've tried work "out of the box" with at least lucid, maverick and natty. When you plug them into the PC, the CD component of the dongle (containing windows software) pops up on the desktop - Ignore this software - you neither want nor need this but "Eject" this cd (rt click eject), wait a few seconds and then go to the network manager applet and set up your connection.


Bouncingwilf

I once had to use something in Canada with Bell's network and they have a connection software.
Am I correct in thinking that no dongle "needs" connection software, they should all be able to connect just by using the APN and appropriate password?

---

### Post by qwertyjjj on 2011-12-09
> **qwertyjjj said:**
> I once had to use something in Canada with Bell's network and they have a connection software.
Am I correct in thinking that no dongle "needs" connection software, they should all be able to connect just by using the APN and appropriate password?

bump

---

### Post by bouncingwilf on 2011-12-13
Apologies, been away. Yes as far as I know, the supplied software is for Windows (and occasionally Mac ) but Linux does not use it. The network connection part of the software is usually built into the modem/sim and Linux picks it up automatically - just accept the network manager defaults.

Bouncingwilf

---

### Post by gandaran on 2011-12-13
> **qwertyjjj said:**
> I once had to use something in Canada with Bell's network and they have a connection software.
Am I correct in thinking that no dongle "needs" connection software, they should all be able to connect just by using the APN and appropriate password?
yes, if you have the correct login authentication details in network manager mobile broadband setup it will work for most dongles, some new ones don't work yet or unless you add the dongle ID to usb-modeswitch configuration

---

### Post by Mark Phelps on 2011-12-13
The answer depends on the specific device, and even then, on the firmware version of the device.

I use an LG VL600 to connect to Verizon's 4G LTE network, and until a few days ago, it automatically connected to the network.

But then, Verizon pushed out a firmware update and now, the device will NOT connect unless the VZAM Access Manager software is run first.  Needless to say, this software ONLY works in Windows.

I tried manually reflashing the device, but it will not accept a firmware downgrade.

So, not every mobile broadband device works with both Windows and Linux.

---

