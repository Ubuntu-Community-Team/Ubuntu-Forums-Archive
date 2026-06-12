---
title: "USB Serial RS 232 Driver"
date: 2009-08-16
forum: General Help
---

### Post by jeff_ro on 2009-08-16
I own a HP nx6110 laptop, which does not have a serial port. I previously purchased a USB to RS 232 adapter but i am unable to to use this without an appropriate driver installed. Does any one have any ideas or locations of where i can obtain a driver. Any help would be greatly appreciated.

---

### Post by caue.rego on 2009-10-01
**No driver needed**.

I'm no expert, but as far as I could experience, Ubuntu *never* needs even to install any file to work with devices. That seems to me, in short, as a legacy from being open and simple, from a well-knowledge person point of view.

I've got a **Prolific USB Serial** that I couldn't make it work with *legit windows xp* (which does pretty good on finding driver updates automatically when you tell it to do so) and its freaking drivers. Nothing on prolific website would help as well - windows already had updated the drivers.

Freaking windows driver are those files with at least 10kb, and up to 100mb (try to install Microsoft webcam). In linux, the "drivers" are usually just a text file or a script telling the system just what's needed with no more than 1kb. That way they all come built in with Ubuntu already.

So, when I tried my usb-to-serial in Ubuntu, all I had to do is plug it in and it was working. Moving from one USB port to another wouldn't trigger a new installation process, because nothing needed to be installed. I even added two programs, one to list devices just to avoid using "lsusb" on the shell, and one for talking with serial. Truly Great! :)

---

### Post by dcstar on 2009-10-01
> **jeff_ro said:**
> I own a HP nx6110 laptop, which does not have a serial port. I previously purchased a USB to RS 232 adapter but i am unable to to use this without an appropriate driver installed. Does any one have any ideas or locations of where i can obtain a driver. Any help would be greatly appreciated.

The Linux kernel will have some support for these devices built into it, but it will depend on the actual device and what chipset is inside it. You will probably find that an established "Brand name" USB-Serial device will work, but some cheaper/new ones will not.

Having the latest version of Ubuntu running the latest kernel will also help as a lot of new hardware will not be supported in old kernels.

---

### Post by shazbut on 2009-10-02
have
```
tail -f /var/log/messages
```
running in a terminal and plug it in to see if it's recognised by the kernal.
I've got one with a prolific chipset that's plug and play, mounts as /dev/ttyUSB0.  You can get them cheap from here:
[http://www.dealextreme.com/details.dx/sku.24512](http://www.dealextreme.com/details.dx/sku.24512)

---

