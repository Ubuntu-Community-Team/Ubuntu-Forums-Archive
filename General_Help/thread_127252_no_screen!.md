---
title: "no screen!?"
date: 2006-02-08
forum: General Help
---

### Post by rich.za on 2006-02-08
Hey all,

I just installed breezy and it shows the graphical module loading but then the colours go all crazy and I can't see a thing.

I looked at the xserver log and it says no screen was detected.

Have tried reconfiguring the xserver to different resolutions but nothing helps.

I have a 19" Flat screen and a GeForce 6600

Please help, need this running asap.

Thanks in advance,
Richard

---

### Post by dcstar on 2006-02-08
[QUOTE=rich.za]Hey all,

I just installed breezy and it shows the graphical module loading but then the colours go all crazy and I can't see a thing.

I looked at the xserver log and it says no screen was detected.

Have tried reconfiguring the xserver to different resolutions but nothing helps.

I have a 19" Flat screen and a GeForce 6600

Please help, need this running asap.

Thanks in advance,
Richard[/QUOTE]
CTRL-ALT-F1 and log in, then:

sudo dpkg-reconfigure xserver-xorg

and select the "VESA" video card, then select the "Simple" option for setting your monitor.

That should get you a basic X system to log into, after that you should look at the /var/log/syslog and messages log files to look for any errors.

---

