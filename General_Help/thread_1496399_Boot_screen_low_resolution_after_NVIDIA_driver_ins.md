---
title: "Boot screen low resolution after NVIDIA driver installation"
date: 2010-05-29
forum: General Help
---

### Post by kOna on 2010-05-29
Hey :)

I've just installed 10.04 on my Dell Latitude D830 with a NVIDIA Quadro NVS 140M; upon booting Ubuntu asked me to install the official NVIDIA driver (latest) so I went ahead and installed it, now the boot splash screen is in about 640x480/800x600 rather than the usual 1920x1200 it was when I first booted.

I'm guessing there is an easy fix for this but I have had a search and can't find a solution!

Any ideas guys?

Cheers,

Kona.

---

### Post by TheDesertDragon on 2010-05-29
Same on my ATi Mobility Radeon HD4650.

Despite the graphics card being completely different as I installed FGLRX, the issue seems quite similar.

Let me guess, your terminals (try pressing ctrl+alt+F1 to F6) are also in this really low resolution, but were high resolution before?

I wouldn't mind a fix to this also! :)

---

### Post by defcon on 2010-05-29
Same problem here. :???:

---

### Post by ratcheer on 2010-05-29
It is a known incompatibility between the proprietary video drivers and the plymouth package. Many threads with many, many posts have discussed it. Personally, I just live with the low-res splash screen and enjoy the desktop benefits of the proprietary driver.

Tim

---

### Post by ceasol on 2010-05-31
Try this workaround, works for me.

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

---

