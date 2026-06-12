---
title: "D-Link DWA-120 for Linux"
date: 2011-02-10
forum: General Help
---

### Post by Odaym on 2011-02-10
i have a D-Link DWA-120 wireless USB adapter that none of the distros are able to familiarize themselves with, not even to be aware of something being plugged in. I have searched [SIZE=2]**[the D-Link website]("http://www.dlink-me.com/?navigation=products&owner=24&product=32&product_details=50")**[/SIZE] and found the driver file and downloaded it, but got this when i tried to unzip it:

> 
Archive:  /home/oday/Downloads/DWA-120_v1.10.zip
[/home/oday/Downloads/DWA-120_v1.10.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/oday/Downloads/DWA-120_v1.10.zip may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/oday/Downloads/DWA-120_v1.10.zip or
          /home/oday/Downloads/DWA-120_v1.10.zip.zip, and cannot find /home/oday/Downloads/DWA-120_v1.10.zip.ZIP, period.



I have also searched [SIZE=2]**[here in this website]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices")**[/SIZE] but have not found my model "DWA-120" in the list provided..
any help would be greatly appreciated.

**PS:** distros i have tried have been RHEL 5, Ubuntu, Mandriva, Fedora {12,13,14}, BackTrack 4...list goes on really

---

### Post by TBABill on 2011-02-10
Can you type ```
lsusb
``` (that's LSUSB in lowercase) into a terminal and paste the output back here so we can see it?

---

### Post by Odaym on 2011-02-10
> 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:0f41 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


the above is **without** the USB attached, and below is **with** the USB attached

> 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 07d1:3a0d D-Link System DWA-120 Wireless 108G Adapter
Bus 002 Device 002: ID 0408:0f41 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


first time i see this, it found it apparently, but on this laptop there's Ubuntu and a built-in Wifi adapter, will i need to attach it to the machine that i want to get this device working on, and **lsusb** there and repost?

---

### Post by TBABill on 2011-02-10
No, this just identified the device. Any computer should identify it the same. I'm trying to find out what chipset this uses. The DWA-140 uses a Ralink chipset I think, but this one appears to use something not supported in Linux (manufacturer did not build a driver for it). That comes from [http://www.dslreports.com/forum/r7775082-B-120-Chipset-~days=365](http://www.dslreports.com/forum/r7775082-B-120-Chipset-~days=365) but that article is quite old (2003). I am still searching for info but you may have to research using ndiswrapper and use the Windows .inf driver instead. Or, just as easy, get an Intel USB wireless device from a place like Ebay for ~$10-15 USD.

---

### Post by TBABill on 2011-02-10
Your card is listed [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link) which led me to
[http://wireless.kernel.org/en/users/Drivers/ar5523](http://wireless.kernel.org/en/users/Drivers/ar5523)
 
The links suggest there is no native driver for the card in Linux and an open source driver is still in development but not available. Your only options are to try the ndiswrapper method or purchase a different device that works with Linux (Intel chipsets, Ralink chipsets work well)

---

### Post by Odaym on 2011-02-10
i'm sorry to be a nuisance, but how do i go about this ndiswrapper approach you're recommending?

---

### Post by TBABill on 2011-02-10
Not a problem. I have never had to use it and I could not find that card as working, partly working or not working so it looks like they may not have even tried it. So you may have to experiment and see if you can get it going. All I can do at this point is offer a link to the ndiswrapper wiki for you to read and see if you can get it going. Others may be able to offer better advice if you continue to struggle with this particular card. [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

---

### Post by TBABill on 2011-02-10
Found this in my search, a how to for that exact device: [http://blog.kasunbg.org/2010/02/make-windows-xp-drivers-work-under.html](http://blog.kasunbg.org/2010/02/make-windows-xp-drivers-work-under.html)

---

