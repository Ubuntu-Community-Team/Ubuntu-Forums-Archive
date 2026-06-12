---
title: "no usable screen configuration"
date: 2011-02-26
forum: General Help
---

### Post by Vi3GameHkr on 2011-02-26
Hello,

I am having a bit of trouble with Xorg on Ubuntu 10.04.  The machine I'm using has the Intel 82845G/GL chipset, if that is of any relevance.  I recently did an upgrade, and upon rebooting, Xorg failed to start, and gave me the following message:
> **Ubuntu is running in low-graphics mode**

The following error was encountered.  You may need to update your configuration to solve this.

(EE) intel(0): No kernal modesetting driver detected.
(EE) Screen(s) found, but none have a usable configuration.

I tried running Xorg -configure and copied the new configure file to /etc/X11/xorg.conf and to no avail.  If I rename /etc/X11/xorg.conf.failsafe to /etc/X11/xorg.conf, I can get a usable display, but it is very limited.  In the failsafe configuration, when I go to System > Prefs > Monitors, it says "Monitor: Unknown" and only gives me a limited number of modes (none of which look right on the HPw17e monitor).  The monitor generally supports 1440X900.

Could anyone give me some tips to somehow fixing this?

Thanks
--Vi3

---

### Post by Vi3GameHkr on 2011-03-01
Does anyone have any information on this?  Is there any kind of work around that will at least put this computer in a usable state?

---

### Post by Vi3GameHkr on 2011-03-03
bump. I still can't figure this out, it is annoying me beyond belief.. I have an urge to switch back to Windows

---

