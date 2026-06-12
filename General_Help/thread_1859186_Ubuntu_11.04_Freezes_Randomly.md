---
title: "Ubuntu 11.04 Freezes Randomly"
date: 2011-10-13
forum: General Help
---

### Post by wfunction on 2011-10-13
I have a VAIO VPCCW27FX/B.
Specs: Core i5 M520; NVIDIA GeForce GT 330M, Atheros AR9285 WLAN, etc.

Ubuntu 11.04 x64 just freezes randomly on my machine -- sometimes I can go into a terminal, sometimes I'm forced to use Alt-PrtSc-REISUB, and sometimes I'm simply forced to do a hard shutdown.

I'm not connected to any networks or anything when this happens, nor am I playing anything that uses the graphics card much (e.g. I was typing into a terminal).

I'm not reinstalling a previous version of Ubuntu, because those versions are pretty unusable (because of driver issues with my machine), so even if they worked, they wouldn't solve the problem.

Sometimes it's within 5 minutes of boot, sometimes it happens half an hour or an hour later.

I've tried reinstalling a billion times now, but it happens every time.
It even happens in VirtualBox on Windows, although I'm not sure if the two are related.

Any ideas?

---

### Post by effenberg0x0 on 2011-10-13
Could you look at your log files, so we can have a hint where to start?
You must look at var/log/dmesg, /var/log/syslog, /var/log/Xorg.0.log mainly. Search for error/warning messages. Try to look for messages close to the time when the crash last happened, then we can have an idea what it is and how to work around it.

Regards,
Effenberg

---

