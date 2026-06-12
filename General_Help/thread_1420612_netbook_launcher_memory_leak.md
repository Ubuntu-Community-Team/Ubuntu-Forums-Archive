---
title: "netbook launcher memory leak"
date: 2010-03-03
forum: General Help
---

### Post by Strongman332 on 2010-03-03
hello all I have been using the netbook launcher on my system for a while now. however i noticed if i live my computer on for a while netbook launcher starts to gain more and more memory space.

has anyone seen this before? any help?

Bug Report found [https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/502730?comments=all](https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/502730?comments=all)


i have include views before and after restarting my pc

---

### Post by Strongman332 on 2010-03-04
bump

---

### Post by tristam77 on 2010-03-27
```

top - 15:01:54 up  7:48,  3 users,  load average: 17.53, 12.08, 10.42
Tasks: 187 total,   5 running, 182 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.9%us,  4.0%sy,  0.3%ni, 51.7%id, 20.6%wa,  1.7%hi,  0.7%si,  0.0%st
Mem:   1014740k total,   994220k used,    20520k free,     5560k buffers
Swap:   706820k total,   705992k used,      828k free,    98808k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                       
 2554 tristam   20   0  968m 488m 1428 R   96 49.3 163:34.04 netbook-launcher
```

Not as pretty a picture...

This happens all the time with my Aspire One ZG5 when i'm logged in to X for some hours.

---

### Post by OpSecShellshock on 2010-03-27
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/358793](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/358793)

Looks like the main fixes are to switch from VESA drivers to the hardware drivers (with acceleration) if you want to maintain the netbook-launcher, or you can switch off of netbook-launcher and just use the regular gnome-panel.

---

### Post by Strongman332 on 2010-03-27
i am  on hard ware rendering. fortunately my cpu is at normal levels. and my computer has more than enough power for this app seeing that it is a gaming laptop. so i don't think my problem is  related. 


found bug report [https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/502730?comments=all](https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/502730?comments=all)

---

