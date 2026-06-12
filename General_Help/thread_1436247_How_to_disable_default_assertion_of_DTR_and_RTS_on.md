---
title: "How to disable default assertion of DTR and RTS on CP210x device?"
date: 2010-03-22
forum: General Help
---

### Post by mathuin on 2010-03-22
I am in the same boat as the author of this blog post:

[http://eksfiles.net/2008/01/rigblaster-plug-play-in-ubuntu-710/](http://eksfiles.net/2008/01/rigblaster-plug-play-in-ubuntu-710/)

I am not able to use the workaround mentioned by the blog post author, so I was hoping to fix the actual problem.

This device uses a Silicon Labs CP2102 device for its USB-serial conversion.  Is there anything I can do (up to and including rebuilding the driver with changes) to prevent RTS and DTR from being asserted by default when the device is open()'ed?  

Ideally it would still be possible to assert and deassert RTS and DTR but if the only fix is to completely disable them for this device I'm okay with that.

Thanks in advance!

---

### Post by wmfa on 2010-07-05
Did you ever have any luck with this?    I'm in the same boat: starting last fall (2009) with a kernel upgrade, it seems that RTS is now always asserted at boot.   Yay.

With about 10 minutes of investigation, it seems that the "new" (1990-ish) RS-232 specification calls for RTS to always be asserted for full-duplex devices.  The problem is when dealing with real-world half-duplex devices, like a radio.  When the machine boots, RTS is asserted, the radio keys up, and at best you only jam the channel and don't burn up your transmitter. 

I would love to see a configuration parameter built into the kernel that could put the device into half-duplex mode.  My guess is that newer programmers don't believe anyone would actually have a half-duplex device these days, so they just changed the protocol from the older RS-232 standard to the new always-RTS mode.

---

### Post by coldraven on 2010-07-05
It has been a long time since I dabbled with serial ports. Could you not just cut off the 9 pin "D" plug then solder on a new one but don't connect the RTS pin?
Voila! semi-duplex!!

---

### Post by wmfa on 2010-07-09
@coldraven:

Thanks for the reply.  Yes, this would work, but that pin serves a very important purpose.  Asserting RTS turns on the radio transmitter.  In order to send data via the radio, the protocol is to assert RTS, send the data, and then turn RTS off.  Basically, the radio interface obeys old-style RS-232 flow control.

Since posting this note just a few days ago, a kernel update appears to have limited (but not fixed) the problem.  Now RTS is raised after boot for probably 15 seconds or so.  It seems there is some kind of timeout that then disables the signal automatically.  

I still would very much like to prevent any activation of the radio, but can't find a setting or parameter that would allow me to do so.  The kernel driver for the CP210x devices does not, itself, raise this line.  Thus the problem is higher in the USB and/or serial protocol layers and I have not had time to trace that code yet.  All suggestions welcome!

---

### Post by wmfa on 2010-08-31
This problem has been addressed in the latest Ubuntu: 10.04.  Kernel is 2.6.32-24.

---

### Post by wmfa on 2010-09-01
> **wmfa said:**
> This problem has been addressed in the latest Ubuntu: 10.04.  Kernel is 2.6.32-24.

I take it back.  Fresh after install, it worked.  After a software update, it's turning my radio on again.  This is driving me crazy.

---

### Post by wmfa on 2012-12-01
Yeah, it's a very stale thread.  But there is a definitive fix.

Firstly, read [https://bugzilla.redhat.com/show_bug.cgi?id=771010](https://bugzilla.redhat.com/show_bug.cgi?id=771010)

The problem is due to ModemManager.  You could remove it, but there is a better way.  The following is specifically for the West Mountain Radio Rigblaster PnP, but this is easily generalized using the USB attributes for a particular device.

Place the following into /etc/udev/rules.d/50-rigblaster-pnp.rules
> 
# Rules for a West Mountain Radio RigBlaster PnP
# 1) force the device to appear as /dev/rigblaster
# 2) prevent ModemManager from activating PTT at  boot time
ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="814a", NAME:="rigblaster", ENV{ID_MM_DEVICE_IGNORE}="1"


---

### Post by wildmanne39 on 2012-12-01
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

