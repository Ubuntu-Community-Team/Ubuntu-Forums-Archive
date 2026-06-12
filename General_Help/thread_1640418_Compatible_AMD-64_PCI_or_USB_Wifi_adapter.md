---
title: "Compatible AMD-64 PCI or USB Wifi adapter"
date: 2010-12-07
forum: General Help
---

### Post by andjarnic on 2010-12-07
Hey all,

Having moved my computers into a "new" office in my house, I have no network cables. Had fun times trying to run a network cable, ultimately stopped due to unknown block in the vertical wall and fear of drilling through something important.

I have strong WIFI signal to this room. I tried plugging in my Netgear WPN111, didn't work. Works on my Win7 box, and I need one on that anyway, so I'd prefer to get another wifi card, be it a PCI, PCIE, or USB dongle. I would prefer the USB dongle since I could then use it elsewhere if need be.

I've installed Ubuntu 10.10 64-bit. The cpu is an Intel quad-core 920, with 8GB ram.

Any ideas would be appreciated.. preferably something I can buy at Best Buy, Fry's or the likes.

---

### Post by gordintoronto on 2010-12-07
I suggest: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Personally, I have a D-Link DWL-G510 PCI card, which "just works." I'm also using Ubuntu 10.10 64-bit.

---

### Post by walt.smith1960 on 2010-12-07
I have 2 USB WiFiN adapters.  Neither works out-of-box, both were pretty easy to get working.  NetGear WNA1100 is a Ath9K based USB adapter.  I used this installer from sourceforge and it works fine:
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)  
The NetGear adapter IS recognized out-of-box in 11.04 alpha1.  I also purchased a TrendNet TEW-649UB which uses a RealTek 8192SU chipset. Again, didn't work out of the box but after finding this bug report & fix:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html) 
I followed the simple directions and am a happy camper with both devices.  Both devices will work on AMD64 installs.  I hope this is of some use to you.

---

