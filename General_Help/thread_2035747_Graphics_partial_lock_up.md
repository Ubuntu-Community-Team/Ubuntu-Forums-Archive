---
title: "Graphics partial lock up"
date: 2012-07-31
forum: General Help
---

### Post by gandaliter on 2012-07-31
I'm running Ubuntu 12.04 on a new desktop machine, and every so often a strange GPU lockup occurs.

First the desktop freezes (i.e. the mouse moves but that's all), then the screen goes black for a few seconds, and then it comes back on, occasionally having reacted to some mouse or keyboard input that had happened during the freeze, but still frozen. This then remains for between 10 and 40 seconds, and then the screen goes black again, and the same thing repeats. Very occasionally the desktop comes up unfrozen for a little while, but it freezes again fairly quickly.

When this is going on I can still ssh in remotely and the system appears fully functional, but nothing I can think of makes the desktop work again, except rebooting.

The video card in an XFX Radeon HD 6950, motherboard EVGA SR-X, and CPU Intel Xeon E5-2630.

Any help would be much appreciated.

gandaliter

---

### Post by 2F4U on 2012-07-31
Are you using the open source or the proprietary ATI graphics drivers? Is this happening when particular applications are running? Did you find any error messages in .xsession-errors in your home directory?

---

### Post by gandaliter on 2012-07-31
I was using the open source drivers, but I've switched to the proprietary ones now to see if it makes any difference. I will post again if it doesn't help.

Many thanks,

gandaliter

---

