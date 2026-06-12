---
title: "Wireless Problems"
date: 2006-01-24
forum: General Help
---

### Post by malkaven on 2006-01-24
Hey all,  

After i upgraded to vanilla 2.6.14ck1 I no longer have wireless for some reason.  I upgraded from 2.6.10.  

My wireless card is a ipw2200
When I do an iwconfig nothings detected, only "lo" and "sit0."

Anyone know how I can get this working?  Did i miss something when I was configuring the kernel?  I followed the howto article to upgrade to vanilla.

---

### Post by cybernmd on 2006-01-24
Same problem here, malkaven. I have followed the guide at this location: [http://doc.gwos.org/index.php/2.6.14_Vanilla](http://doc.gwos.org/index.php/2.6.14_Vanilla) to compile 2.6.14ck1 from scratch. After the reboot both of my network cards were no longer working(wlan0) or disappeared completely (ipw2200). I have tried recompiling both ieee80211 and ipw2200 modules from scratch. Unfortunately that still did not fix our problem ;(.  Any feedback is appreciated.

---

### Post by casper_2095 on 2006-01-24
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
[http://ipw2200.sourceforge.net/INSTALL](http://ipw2200.sourceforge.net/INSTALL)

5.  KERNEL REQUIREMENTS - Configuration
-----------------------------------------------

Your kernel must be configured and compiled to provide certain capabilities
needed by the ieee80211 and ipw2200 drivers.  

In addition, [B]kernel versions 2.6.14 and later are providing *old* ieee80211
and ipw2200 1.0 drivers as part of the mainline tree.  If these are compiled
into your kernel (i.e. not as modules, but as built-in),[/B] you will need to
re-configure (using n to exclude/disable ieee80211 and ipw2200) and rebuild
your kernel before proceeding with your ipw2200 upgrade.  See below.

You can verify that your running kernel is configured properly by
searching the following file for the #define entries described below:

	/lib/modules/`uname -r`/build/include/linux/autoconf.h

---

