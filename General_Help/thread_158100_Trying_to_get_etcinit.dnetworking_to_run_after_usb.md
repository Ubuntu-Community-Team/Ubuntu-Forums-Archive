---
title: "Trying to get /etc/init.d/networking to run after usb devices are recognized"
date: 2006-04-10
forum: General Help
---

### Post by frikazoyd on 2006-04-10
Hello all,

I've got Breezy ubuntu installed on a box I'm using as a MythTV DVR.  To keep things simple and cheap (and because I don't have enough PCI ports), I ended up getting a wireless USB device.

I've got it set up pretty well so far so that if the machine gets so borked that it needs a reboot, all anyone has to do is hold the power button to get it to shut down, and then turn it back on.

The trouble is with getting the wireless internet to start up with the machine.

Every time I reboot the thing, wlan0 is set up and ready to go, but is not activated.  I don't have anything else set up, and wlan0 is the default device.  And when I activate it (or even if I run ifup wlan0 from the terminal) everything is up and running fine.  The only thing I can think of that would be causing this is if the usb devices aren't detected when the system is running the "networking" startup script, and so it isn't able to get to wlan0 yet.

So, does anyone know an easy fix for this?  Maybe some way to get /etc/init.d/networking running as the last thing, or maybe someone knows the last thing run so I can tack on "ifup wlan0" on it?

Thanks in advance

---

### Post by frikazoyd on 2006-04-10
I just stuck "ifup wlan0" at the front of the /etc/init.d/gdm script and it seems to have fixed my problem.

---

