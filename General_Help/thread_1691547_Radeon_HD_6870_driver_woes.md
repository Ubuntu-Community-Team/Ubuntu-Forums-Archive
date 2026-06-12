---
title: "Radeon HD 6870 driver woes"
date: 2011-02-20
forum: General Help
---

### Post by great_cthulhu on 2011-02-20
**Ignore Unless others are having the same problem**
RMAed the card, so it's no longer an issue for me, at least.

I'm having a few problems getting my Radeon HD 6870 to work at all under 10.10 (64 bit).

Other than the aforementioned graphics card, relevant hardware is:
AMD Phenom II x6 1090T proc
ASUS M4A89GTD PRO/USB3 AM3 AMD mobo

After installing (getting basic VGA only), I initially enabled "proprietary drivers", rebooted, and had a nice black screen that was all blue pinstripey.

Nuked all proprietary drivers, then attempted again with the advice given here:
[http://justbloodywork.blogspot.com/2010/12/amdati-drivers-for-radeon-hd-6870-on.html](http://justbloodywork.blogspot.com/2010/12/amdati-drivers-for-radeon-hd-6870-on.html)

X ends up getting hosed, again dumped proprietary drivers and xorg.conf

Try again with the instructions given here:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Restricted_Drivers_Manager](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Restricted_Drivers_Manager)

Same again, X go boom, remove all proprietary drivers nuke xorg.conf.

So then I grabbed the ati drivers and utilities from the restricted repo.  Installed everything through there, made sure to run aticonfig-i, restarted, and I'm back at the pinstripes.

Is there anything else I should try before just RMAing the damned card?

---

