---
title: "Suddenly can't connect Broadcom wireless"
date: 2012-02-11
forum: General Help
---

### Post by lykwydchykyn on 2012-02-11
I have a Dell Latitude e5500 with a broadcom bcm4312 wireless.

My home network is using Wireless G with wpa-psk security.

I'm running Oneiric and using nm-applet to connect.  

It's worked fine for years.

Suddenly, last night, it stopped connecting.  When I try to connect it just spins and spins and asks me repeatedly for the passphrase.

I tried connecting manually with wpa_supplicant and it fails.

I tried disabling all security on the router, and it still fails.

Finally, I booted to another distro (TinyCore CorePlus) and it connects with no problems.  Since tinycore uses the old b43 driver, I tried removing the broadcom-wl driver and inserting the broadcom-b43 driver.  This, amazingly, worked (and I'm posting from my laptop now using it).

So my question is, does anyone have an idea why the wl driver is suddenly failing?  Isn't it the newer "better" one?

---

