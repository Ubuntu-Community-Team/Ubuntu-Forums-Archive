---
title: "Splash screen for 1366x768"
date: 2010-06-21
forum: General Help
---

### Post by cwwilson721 on 2010-06-21
The default Ubuntu Lucid install only uses a 640x480 splash screen, but the Live CD displays a splash correctly at 1366x768.

I've installed/tried Startup Manager, but if I change the resolution to anything but 640x768/16bit, my Nvidia screen gets garbled, until the xserver comes up.

I know it's possible, because of the live cd. Any ideas?

---

### Post by cwwilson721 on 2010-06-28
{Bump for 0 replies}

---

### Post by tuxedosteve on 2010-08-07
I have the same issue on a Dell Studio One 19.  1366x768 display.  Splash screen looked good until I loaded the Nvidia restricted drivers.  Gnome display looks good, but Ubuntu splash is stretched and poopy.

Nvidia driver version 195.36.24 NV-CONTROL 1.22
GeForce 9200 512MB integrated

---

### Post by Mze on 2010-08-07
see if this [article]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") helps

---

### Post by tuxedosteve on 2010-08-07
> **tuxedosteve said:**
> I have the same issue on a Dell Studio One 19.  1366x768 display.  Splash screen looked good until I loaded the Nvidia restricted drivers.  Gnome display looks good, but Ubuntu splash is stretched and poopy.

Nvidia driver version 195.36.24 NV-CONTROL 1.22
GeForce 9200 512MB integrated

Disabled the Nvidia driver and everything is much better.  System seems a bit more snappy and responsive, strange and random screen artifacts in top panel and menu are gone, splash is displaying nicely again, some dialogue buttons are now clickable again after seeming randomly useless before... but no fancy 3D effects :(  
Guess I can live with that.

Heh, I quoted myself.  :lolflag:

---

