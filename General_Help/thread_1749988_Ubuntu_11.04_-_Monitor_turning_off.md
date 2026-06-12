---
title: "Ubuntu 11.04 - Monitor turning off"
date: 2011-05-05
forum: General Help
---

### Post by KnightOnline on 2011-05-05
Hi Everyone,

I just did a clean install of Ubuntu 11.04 on my PC. Installation went smoothly, and I can boot it and log in.

If i leave it there running, nothing happens, but as soon as i try to run an application (Firefox, Update Manager, etc), the screen turns off and I can't do anything else anymore except reboot.

I was able to apply the latest updates using apt-get update from the terminal (one of the very few apps that doesn't turn the screen off), but can't get rid of the problem, what can i do????

My PC is a Intel Core i5 PC with a Nvidia Gefore 210 graphics card.

I was able to install the proprietary drivers for Nvidea, no change. Both Unity and "Ubuntu Classic" have this issue 

Thanks in advance for any insight

---

### Post by spikoley on 2011-05-06
This might be related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  Check under Additional Drivers for "This driver is activated but not currently in use".  If you see that message then add your information to the bug report.

---

