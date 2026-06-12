---
title: "Wake on Lan issue"
date: 2010-08-27
forum: General Help
---

### Post by sr_guy on 2010-08-27
Running Ubuntu 10.04

Based on this guide, _[http://ubuntuforums.org/showthread.php?t=360901](http://ubuntuforums.org/showthread.php?t=360901)_ I have WOL working, but to a certain degree. I set my MB bios up, installed the appropriate apps, setup rc.local to start ethtool -s eth0 wol g. I sent a wakeuplan command from another machine and the PC started up.

The only issue is that when it comes out of hibernate from the wakeonlan request eth0 doesn't autoconnect, so if I try to remotely wake it, once it boots into the gui eth0 will remain disconnected until I manually start it. Any way to fix this?

---

### Post by tgalati4 on 2010-08-27
Have you set up a static IP address for the machine?  That sometimes works better because of timeout issues with dhcp requests.

---

### Post by sr_guy on 2010-08-28
Static IP is setup on my router (DD-WRT). Forces a static ip to that box bsed on ts mac id.

This issue ONLY happens if the box hibernates or goes into power saving mode

---

