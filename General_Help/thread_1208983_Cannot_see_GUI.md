---
title: "Cannot see GUI"
date: 2009-07-09
forum: General Help
---

### Post by brianfast on 2009-07-09
Hi I switched out my ATI 2600xt for a geforce 9600 GSO today. Unsuprisingly when I booted ubuntu, X didn't load correctly. I am using 9.4 64. How do I change x to use VESA or NV?

I am very disappointed so far. dpkg-reconfigure xserver-xorg didn't do anything. Manually editing xorg.conf did nothing (it was in a wierd default state too).

This is way too complicated... All I want are crappy VESA graphics.. how do I get this?

---

### Post by wpshooter on 2009-07-09
Find someone that is running a geforce 9600 GSO and get them to send you a copy of their xorg.conf file.  Or reinstall Ubuntu.  Hope you have everything backed up.  Should have if you were going to switch video cards.

---

### Post by Yellow Pasque on 2009-07-09
If you had fglrx/Catalyst drivers, make sure you purge them: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show)

---

### Post by brianfast on 2009-07-09
Reinstall Ubuntu to fix graphics? No thank you...

---

### Post by wpshooter on 2009-07-09
> **brianfast said:**
> Reinstall Ubuntu to fix graphics? No thank you...

Let us know if & how you get it fixed.

Thanks.

---

