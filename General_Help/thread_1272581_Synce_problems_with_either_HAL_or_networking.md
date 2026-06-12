---
title: "Synce problems with either HAL or networking"
date: 2009-09-22
forum: General Help
---

### Post by Muzer on 2009-09-22
OK, I've got Synce working with advanced networking both enabled and disabled, however, there are problems with both.

Without advanced networking disabled (ie ppp mode), it works fine. However, if I replug the phone or go into ICS (internet connection sharing) and back, I need to restart HAL (sudo /etc/init.d/hal restart) before it will let me use synce again. This is obviously rather annoying. The error I get is:

** Message: Device /org/freedesktop/Hal/devices/usb_device_bb4_a13_3fbf5000_7351_0801_3575_590161836950_if0_serial_usb_0_0 not fully set in Hal, skipping



With advanced networking enabled (rndis mode), it again works fine. However, it prevents me from accessing the internet since it creates a networking interface rndis0 that gets an IP, with a higher priority (presumably) than wlan0. I do not want to permanently blacklist rndis0, since it is also the interface that is used in ICS (internet connection sharing) on the phone and I need that. However, would there be a way to give wlan0 and eth0 a higher priority than rndis0 if they are connected and have IPs?







An answer to either or both of these would be appreciated (I only need an answer to one though).

---

### Post by Muzer on 2009-09-22
*bump*

I assume it's OK to bump posts here? It's on the 4th page already!

---

