---
title: "Playstation 3 Controller in 9.10 Karma Netbook remix"
date: 2010-01-23
forum: General Help
---

### Post by cleverghost on 2010-01-23
First of all, these are the two webpages I have read about this, and I have done every step, with bluez 4.51. 

[https://help.ubuntu.com/community/Sixaxis]("https://help.ubuntu.com/community/Sixaxis#Requirements")

[http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu](http://www.wiredrevolution.com/ubuntu/setup-ps3-controller-over-bluetooth-on-ubuntu)

Now, I have gone through the setup procedure -successfully- (no errors) repacked the patch into the deb with a little figuring out.. but once I do this . . . 

```
sudo hidd --server --nocheck -n

```and turn on my controller, bluetooth not only enables again and gives me this annoying popup to reject or allow every 2 seconds (even if I check always allow), I get no output unless I Ctrl+C...

```
hidd[14928]: Bluetooth HID daemon

##(after this I ctrl+c'd and got...)
^Chidd[14928]: New HID device 00:24:33:79:B3:04 (Sony Computer Entertainment Wireless Controller)
hidd[14928]: Failed to enable sixaxis
hidd[14928]: HID create error 9 (Bad file descriptor)
hidd[14928]: Exit

```Another thing, when I have the ps3 controller hooked up via USB, jscalibrator is saying it is a X-Box 360 gamepad (which I do have one, and attempted to get working, before I realized the triggers were actually axis, and that PSXC will not take the buttons correctly)


Phew. Okay, so onto my hardware

I am running the following:

Acer Aspire One Netbook aoa150-1447
Intel Atom 270
1 GB Ram
160gb HDD
Rocketfish Bluetooth USB dongle RF-FLBTAD
PS3 SIXAXIS wireless bluetooth controller

All this is running on the AMAZING netbook remix XD

If anything else is needed, I am pretty much going to be camping this thread. Thanks!

---

### Post by cleverghost on 2010-01-23
The popup I get when I press the PS button when its disconnected from the usb is titled:

Grant access to '00001124-0000-1000-8000-00805f9b34fb'

---

### Post by cleverghost on 2010-01-23
SOLVED 


Download QtSixA, worked like a charm.

---

