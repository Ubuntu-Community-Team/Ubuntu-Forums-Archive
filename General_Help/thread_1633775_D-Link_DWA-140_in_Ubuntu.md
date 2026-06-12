---
title: "D-Link DWA-140 in Ubuntu?"
date: 2010-11-29
forum: General Help
---

### Post by NDAC on 2010-11-29
Hello! 

I'm thinking about formatting my Windows installation and start using Ubuntu instead. But there's just one problem, last time I tried I couldn't get my WLAN to work (Ubuntu 10.04). 

It's a D-Link DWA-140 dongle, I searched the forum and I found a post that was well over 2 years old and the links are all dead. So no help there. 


So has anyone got the DWA-140 to work with Ubuntu?

---

### Post by ki4jgt on 2010-11-29
Have you tried NDISWrapper?

---

### Post by NDAC on 2010-11-30
No. But I just looked NDISWrapper up, and it don't seem to support the chipset. Well, atleast not according to [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB)

But yeah, I don't know if it shares the same chipset as any of the mentioned USB dongles?

---

### Post by jonandtice on 2010-12-20
Hope this doesn't get to you too late.  I have the DWA-140 and to get it to work I had to blacklist the rt2800usb driver.  It was loading that as well as the rt2870sta which is the one that works.  All you should have to do on an existing install is add the line ```
blacklist rt2800usb
``` to /etc/modules.d/blacklist.  Reboot and it should work.

---

