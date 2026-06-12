---
title: "Ubuntu hangs during boot. kernel 3.0.0-14 3.0.0-15"
date: 2011-12-21
forum: General Help
---

### Post by SonicSteve on 2011-12-21
Concerning Ubuntu 11.10 I've noticed that there are many help requests on the net from people with hanging ubuntu systems after upgrading the kernel from 3.0.0-13 to -14 or -15.

For a while now I was in that boat and had to manually select the -13 kernel to boot up properly. After spending some time tinkering I've found a fix that at least worked for me. 

In many BIOS's there is an option for configuring whether or not your system has a "plug and play" aware OS. Mine was set to no. While this usually doesn't cause any problems these latest kernel update don't seem to like it. 

I switched mine from NO to YES and the I'm now using the 3.0.0-15 kernel. 

If you don't know how to get into your BIOS it can be done just after you turn your computer on. If you start loading Ubuntu you've let your system load too far. Just after turning on the system pressing the "del" key is most typical, however every system builder is different and I've seen F1, F10, ALT + some other key combinations also. If in doubt do a google search for brand of your computer, and BIOS. 

Hopefully this helps a few people.

---

