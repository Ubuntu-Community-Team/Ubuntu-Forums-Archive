---
title: "High memory usage after screen lock"
date: 2009-07-06
forum: General Help
---

### Post by tarlos25 on 2009-07-06
I recently install Kubuntu 9.04 AMD64, upgraded everything to current, Amarok to 2.1, added some themes, Oxygen system monitor, configured for workplace (Samba/LDAP domain logins).  In normal usage, everything seems completely fine.

However, I lock the screen at night, and when I come back, kwin has drastically increased its CPU usage.  It's not too bad after a single night, though I've had to restart the X server several mornings, but over the weekend, my system was basically unusable.  I was unable to get the screen unlock dialog to even appear at first.  Switching to a CLI terminal allowed me to see that dbus-daemon was at approximately 52% memory usage (4 GB RAM installed, /proc/meminfo shows 3860584 kB).  When I switched back to the X terminal, the unlock screen dialog was up, so I unlocked the screen.  The system at this point was barely usable, so I switched back to the CLI terminal and rebooted.  As expected, everything is working fine now.

I had the following applications open:  2 Kate sessions, one Konsole, Thunderbird, Amarok (not playing anything, just open), and the basic system processes.  The logs show no access over the weekend.  I am using the picture slideshow screensaver, the pictures being accessed are on an NTFS partition, however, I observed this behavior while using the blank screensaver that was the default.

Can anyone offer some advice (other than logging out or rebooting when I leave)?

---

