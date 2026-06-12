---
title: "Bluetooth USB dongle (USB in general)"
date: 2009-07-03
forum: General Help
---

### Post by bobtown on 2009-07-03
I'm trying to get my Bluetooth USB dongle (IOGear GBU421) to work in Ubuntu 9.04 but I'm getting no where.  I've tried several "walkthroughs" I found around the 'net, including installing *blueman* which I had hopes for.  I was able to see it once from a XP laptop after installing the "Bluetooth File Sharing" program, but I wasn't able to connect and was never able to see the Ubuntu machine again through Bluetooth.

When I plug in the dongle and list USB devices I get...

```
Bus 001 Device 004: ID 07d1:3c04 D-Link System WUA-1340
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[B]Bus 002 Device 011: ID 0a5c:2148 Broadcom Corp. 
Bus 002 Device 010: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 009: ID 0a5c:4502 Broadcom Corp. 
Bus 002 Device 008: ID 0a5c:4500 Broadcom Corp. [/B]
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 046d:c313 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```From others posts, it seems like I should be seeing a little more of a description from the dongle than "Broadcom Corp."  I'm wondering if there is something more fundamentally wrong with the setup and if anyone has any advice.  The dongle works in XP, so it doesn't appear to be a hardware issue.

I don't consider myself a Linux guru, so please be gently.

Thanks

---

### Post by Chronon on 2009-07-03
Nah.  That's how it appears on my netbook and it works fine.

I use bluez and it works.

---

### Post by fragos on 2009-07-03
What version of Ubuntu are you running? Bluetooth support has gotten better and more strait forward with each new Ubuntu release.

---

### Post by Hobgoblin on 2009-07-03
> **fragos said:**
> What version of Ubuntu are you running? Bluetooth support has gotten better and more strait forward with each new Ubuntu release.

> **bobtown said:**
> in Ubuntu 9.04

Do you get the Bluetooth icon in the notification area?

What do you get if you do **dmesg** after plugging it in?

Looking at the output of lsusb on my system I suspect your dongle is not supported.

---

### Post by Chronon on 2009-07-03
I am successfully using this specific dongle (GBU421) with Jaunty (UNR) on a Eee PC 1000HEB.

---

### Post by Diznix on 2009-08-20
Hi, I am also using the GBU421, under the Latest Netbook Remix 9.04 Jaunty
I also cannot get any of the services to work, i do get the notification and BT icon when i plug in the unit, and the unit remains lit.  My lsusb reports the same values as the first post... i am a very very new user to ubuntu/linux in general...  Is there something i am missing/overlooked for the install/control of this BT devices?

Any help would be greatly appreciated!!

Acer Aspire One netbook
AOA150
N270

---

### Post by fragos on 2009-08-20
> **Diznix said:**
> Hi, I am also using the GBU421, under the Latest Netbook Remix 9.04 Jaunty
I also cannot get any of the services to work, i do get the notification and BT icon when i plug in the unit, and the unit remains lit.  My lsusb reports the same values as the first post... i am a very very new user to ubuntu/linux in general...  Is there something i am missing/overlooked for the install/control of this BT devices?

Any help would be greatly appreciated!!

Acer Aspire One netbook
AOA150
N270

When you right click the BT icon and select Preferences are your devices in the known devices list?

---

### Post by Diznix on 2009-08-20
When i right click on the BT emblem, the one that starts with the insertion of the dongle... I do not get any devices, also when i go to set up a device it does not see any in that window/menu either.  I have downloaded and installed pretty much all the BT refrenced packages in the synapse area and the kdebluetooth4 executes with no tray icon or any real notification of activation/falure, the bluetooth control program tells me that the inquiry times out, and the scan all 30 channels function returns that all of the channels are closed/denied.  One note on this though, all of the services in the aformentioned programs that involve "scanning" of any sort will report that there is no device if i unplug the dongle and try the same process.  And the standard bt icon that pops up will go away.  SO it seems that it sees it on the usb/knows what it is.  But for some reason the services and dongle are not talking to each other properly.

---

### Post by fragos on 2009-08-20
> **Diznix said:**
> When i right click on the BT emblem, the one that starts with the insertion of the dongle... I do not get any devices, also when i go to set up a device it does not see any in that window/menu either.  I have downloaded and installed pretty much all the BT refrenced packages in the synapse area and the kdebluetooth4 executes with no tray icon or any real notification of activation/falure, the bluetooth control program tells me that the inquiry times out, and the scan all 30 channels function returns that all of the channels are closed/denied.  One note on this though, all of the services in the aformentioned programs that involve "scanning" of any sort will report that there is no device if i unplug the dongle and try the same process.  And the standard bt icon that pops up will go away.  SO it seems that it sees it on the usb/knows what it is.  But for some reason the services and dongle are not talking to each other properly.

BT devices may require some manual action to initiate pairing. May cell phones for example always allow connection to a paired trusted device but to enable pairing you have to turn the discovery function on. That function will time out on it's own.

---

### Post by noone_special on 2009-09-26
I just installed jaunty on my tower pc made from an old hp (hp is crap I know but I found it in a junk yard because buying a comp is out of reach for now) it wont even recognize the iogear bt usb dongle its becomeing quite a pest seeing how I'd love to use my sixaxis ps3 controller for games and such maybe even a mouse but it keeps giving me  the same err code (err 71) I'm not sure what this is but wee need some one to fix it these tiny dongles come very handy :guitar:

---

### Post by jaypmcwilliams on 2009-12-22
ok, same prob. It does NOT pair! it recognizes the dongle but NO devices. did same as others. found it's a prob based on the kernel. was not included, addressed & fixed until karmic 9.10. Older USB Bluetooth dongles work GREAT. I'm using Intrepid 8.10 AMD64. PROBLEM with karmic is they dropped a LOT of xorg & xserver driver support for other slightly older hardware (i.e. ATI Radeon X1200 video, etc.). NOT COOL!!!!!!!!!!!!!!!!!!!!!!! NOT supporting karmic because of these issues. Ironic, karmic is creating BAD karma.

---

