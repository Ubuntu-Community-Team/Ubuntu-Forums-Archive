---
title: "Wireless firmware for Dell"
date: 2011-04-02
forum: General Help
---

### Post by Teegoo on 2011-04-02
It seems my Ubuntu is lacking wireless firmware.

My card info:

```
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```


Is the firmware already there, and just not installed? Or do I need to download it?

---

### Post by davidmohammed on 2011-04-02
you didnt say which version of ubuntu you are running.

Have you looked to see if there are any administrator - hardware drivers to activate.  Normally for your type of wireless card you just activate the broadcom driver from that window.

---

### Post by treehermit on 2011-04-02
If you are using the Maverick Meerkat 10.10 version, you can install the package  'Additional Drivers' from the Software Center.

This package will detect all proprietary drivers for your Dell hardware.

I'm not sure if the package is available in previous versions of Ubuntu but you can try looking it up.

Best of Luck

---

### Post by Teegoo on 2011-04-02
> **davidmohammed said:**
> you didnt say which version of ubuntu you are running.

Have you looked to see if there are any administrator - hardware drivers to activate.  Normally for your type of wireless card you just activate the broadcom driver from that window.


Ah! You were right. All I needed was a wired connection. Thanks!

---

