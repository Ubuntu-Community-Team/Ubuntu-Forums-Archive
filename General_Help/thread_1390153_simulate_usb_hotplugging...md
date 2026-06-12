---
title: "simulate usb hotplugging.."
date: 2010-01-25
forum: General Help
---

### Post by beyond_ah on 2010-01-25
Hi,

I'm looking for a way to simulate the plugging in of usb devices. I tried using 'restart udev', but that didn't have the desired effect.

Context is an application which uses a couple of usbdevices. These usbdevices seem to disconnect every now and then. I have an error handler which detects these disconnects and I'd like to simulate a hotplug of the devices so the application can continue it's work without human intervention and minimal downtime.

Any ideas?

Thanks!

---

