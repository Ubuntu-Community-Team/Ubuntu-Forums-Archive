---
title: "NDISWrapper Problem (Belkin Wireless)"
date: 2006-03-25
forum: General Help
---

### Post by rianquinn on 2006-03-25
I have installed ndiswrapper and the BCMWL5.INF file (for Windows XP), and ndiswrapper shows the driver and hardware present. When I modprobe ndiswrapper though, the light on the pcmia device doesn't come on. What am I missing?

---

### Post by Titus A Duxass on 2006-03-25
first,
Add ndiswrapper to your /etc/modules file (do it at the command line)
Then go and configure your card through networking.
You also need to edit your /etc/network/interfaces file, do a search for examples or find a good wireless howto.
Then shutdown and down a cold boot.

Watch your card lights on start up and report back.

---

