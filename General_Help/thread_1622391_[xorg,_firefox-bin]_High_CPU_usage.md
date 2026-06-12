---
title: "[xorg, firefox-bin] High CPU usage"
date: 2010-11-15
forum: General Help
---

### Post by #define on 2010-11-15
In Firefox, when I scroll _any_ page, processes Xorg & firefox-bin eat one of CPU's cores up to 100%.
(Xorg - 60%, firefox-bin - 40%)
In Chromium it is Ok.
Ubuntu 10.10 64bit, *Firefox 3.6.12, Ati Catalyst 10.9*

---

### Post by daniferi on 2010-12-12
Same problem for me. It seems when firefox is running and i opening new tabs or i making some window-operating (minimize, maximize) the firefox and xorg eat my cpu for a sec. Cpu usage goes up to 90-95% and everything are stopped for a moment. It is not funny when music breaks like on old turntables :) Now i using opera for testing and there is no problem. With 10 opened tabs i can do anything without extreme cpu usage.

System: Ubuntu 10.04 32bit
VGA: ATI Radeon HD 3650 (Catalyst 10.11)
Browser: Firefox 3.6.13

Some additional info: I changed my VGA in last few days and the previous card was an Nvidia Geforce 7600GS and this problem has started now. It may be some fglrx-firefox-xorg incompatibility?

**Edit: **It seems this is a bug: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/38131](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/38131)

---

### Post by paulmostertman on 2011-03-31
> **daniferi said:**
> Same problem for me. It seems when firefox is running and i opening new tabs or i making some window-operating (minimize, maximize) the firefox and xorg eat my cpu for a sec. Cpu usage goes up to 90-95% and everything are stopped for a moment. It is not funny when music breaks like on old turntables :) Now i using opera for testing and there is no problem. With 10 opened tabs i can do anything without extreme cpu usage.
 
System: Ubuntu 10.04 32bit
VGA: ATI Radeon HD 3650 (Catalyst 10.11)
Browser: Firefox 3.6.13
 
Some additional info: I changed my VGA in last few days and the previous card was an Nvidia Geforce 7600GS and this problem has started now. It may be some fglrx-firefox-xorg incompatibility?
 
**Edit: **It seems this is a bug: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/38131](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/38131)
 
XOrg takes up 100% processor time, its not firefox fault. It is a driver problem, after updating ubuntu it still uses the old video drivers. To solve this go to system > Administration > Additional Drivers and install the newest drivers for your video card > in my case: the current version.
Problem Solved,
 
Greetings,
Paul Mostertman 
[www.linuxportal.nl]("http://www.linuxportal.nl")

---

