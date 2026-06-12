---
title: "Dead wireless card?"
date: 2009-08-23
forum: General Help
---

### Post by bchurchill on 2009-08-23
My wireless internet was running smoothly, until one day it suddenly stopped while browsing the web.  I've checked my configuration (I've set it up manually, no network manager), and everything *seems* to be setup fine.  The problem is that:

```

#iwlist wlan0 scan
wlan0          No scan results

```Nonetheless, my other computers detect at least four wireless networks.

I'm quite sure that my firmware and driver is reasonably up-to-date, because I had to install that to get my wireless working in the first place.  It's a Broadcom BCM94318 that's about four years old.  Do you think it's dead?  Or are there some other things I can try?

---

### Post by bodyharvester on 2009-08-23
have you tried installing, say, this one?  [http://www.wireless-driver.com/download/broadcom/2007-6-26/Broadcom-BCM94318MPG-Mini-PCI-Driver.htm](http://www.wireless-driver.com/download/broadcom/2007-6-26/Broadcom-BCM94318MPG-Mini-PCI-Driver.htm)

you may need to use "ndiswrapper" as im assuming itll be for Windows

---

