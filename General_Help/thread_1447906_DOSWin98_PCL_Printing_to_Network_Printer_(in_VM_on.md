---
title: "DOS/Win98 PCL Printing to Network Printer (in VM on Ubuntu host?)"
date: 2010-04-05
forum: General Help
---

### Post by BikeHelmet on 2010-04-05
Hello there. :)

I have a friend whose business is stuck on some old DOS program. It's one really old billing program with the parallel port licensing dongle, and all that.

I would like to migrate it to Ubuntu, perhaps running Win98 in VMware/Virtualbox - but before I do that, I have some challenges that must be overcome.

The biggest of which is printers. I have a really nice Brother HL-2170w network/wireless greyscale laser printer. It works great with Windows (2000 - Win7), OSX, and Linux - it does not, however, have Win98 drivers.

The billing software is DOS-based, and apparently can communicate to any PCL5 or PCL6 printer. (I'm unsure which, but will look it up before proceeding, obviously)

This means that the 2170W with its PCL support should be compatible with the DOS program - but I can't get it to show up in Windows 98, because no drivers exist.

Since I'm unsure where to ask, I figured I'd ask here. Surely most of this community used Win98 at some point. ;) 

Is there a way to tunnel network printer traffic for a printer with no drivers to an LPT port, so the DOS program can directly access it, and I can work towards migrating to a brand new Ubuntu PC? 

:popcorn:

Much appreciation to anyone that can point me in the right direction.

---

### Post by dcstar on 2010-04-06
> **BikeHelmet said:**
> Hello there. :)

I have a friend whose business is stuck on some old DOS program. It's one really old billing program with the parallel port licensing dongle, and all that.

I would like to migrate it to Ubuntu, perhaps running Win98 in VMware/Virtualbox - but before I do that, I have some challenges that must be overcome.

The biggest of which is printers. I have a really nice Brother HL-2170w network/wireless greyscale laser printer. It works great with Windows (2000 - Win7), OSX, and Linux - it does not, however, have Win98 drivers.

The billing software is DOS-based, and apparently can communicate to any PCL5 or PCL6 printer. (I'm unsure which, but will look it up before proceeding, obviously)

This means that the 2170W with its PCL support should be compatible with the DOS program - but I can't get it to show up in Windows 98, because no drivers exist.

Since I'm unsure where to ask, I figured I'd ask here. Surely most of this community used Win98 at some point. ;) 

Is there a way to tunnel network printer traffic for a printer with no drivers to an LPT port, so the DOS program can directly access it, and I can work towards migrating to a brand new Ubuntu PC? 

:popcorn:

Much appreciation to anyone that can point me in the right direction.

Simply install the printer (with the IP address) and use a different Brother printer driver.

Older printer drivers usually work with newer printers, except you may just miss out on newer printer features.

---

### Post by BikeHelmet on 2010-04-07
Well, that didn't work. Seems like Windows 98 doesn't like printing to IP. I tried hooking it up directly, and using an older printer driver. Apparently the HL-2170w supports [HP Laserjet emulation]("http://welcome.solutions.brother.com/BSC/public/us/ca/en/faq/faq/000000/000100/000080/faq000180_000.html?reg=us&c=ca&lang=en&prod=hl2170w_all&Cat=5") - but the DOS program only wants to send to LPT1, and not to USB. I couldn't figure out a way to direct it to the USB port. My limited Windows 98 knowledge is really failing me right now.

My next thought was a Parallel Port to USB converter cable, but I couldn't find one on Google(just the other way around), so... more experimentation and brainstorming. :)

---

### Post by BikeHelmet on 2010-04-08
Okay, got it working. One firmware update (via USB), then back to networked wireless. Win98 seems to only work with hostnames - not IPs. I ended up sharing the printer over Samba from my NAS, and then was finally able to detect it.

After that, I set Win98 to use **HP Laserjet 4** drivers. It prompted to capture LPT1. I told it to use LPT2, and can toggle LPT1 capture on and off, depending on whether I want to use the new or old printer with the DOS program.

It seems to be working well now. There are a few issues with  Samba shares - Win98 starts to chug after a minute, almost like it's consuming 100% CPU - but I'm guessing Google will reveal answers to that as well.

The printer issues *seem* to be totally resolved. :)

Poor guy though - now he needs a NAS. ;)

---

