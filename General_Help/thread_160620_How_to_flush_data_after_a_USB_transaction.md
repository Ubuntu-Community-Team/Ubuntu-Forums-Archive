---
title: "How to flush data after a USB transaction?"
date: 2006-04-15
forum: General Help
---

### Post by matthias_k on 2006-04-15
Hi,

I noticed a very annoying thing when copying data to a USB mass storage (memory stick, memory card, whatever) with Nautilus:

Instead of really copying the data to the device, Nautilus will merely copy the information (?) about the new files to the device, but not all the data itself. Don't know how to explain this better, I'm not a developer, but it has some very annoying side effects, for example:
- After immediately unplugging the USB device, the data is NOT present on the device; you usually have to wait some time for it to be actually copied in the background...
- When copying large amounts of data, the visual transfer (e.g. by dragging and dropping) is ridiculously fast, but if you shut down your system immediately thereafter, it seems to "freeze" for a minute or more and actually start flushing the data to the device... at first, I thought my system had crashed until I realized this, because no message is given on the screen about what it's actually doing

This, simply put, sucks. It's the Microsoft way of doing things: Trying to trick the user into thinking the transfers are ultra fast, but in fact nothing is really copied (at least not to the USB device).

Can I turn off this caching somewhere, such that all data is directly copied to the device? Or at least some command which allows me to flush it to the device when *I* want?

Thanks,
Matthias

---

### Post by Ramses de Norre on 2006-04-15
Type sync in terminal to clear all write caches.
You can mount a device with the sync option (default is async) but the problem is that usb devices are automounted, I don't know how to change the defaults on that.

---

### Post by matthias_k on 2006-04-15
Well, thanks, that's pretty much what I was looking for!

---

