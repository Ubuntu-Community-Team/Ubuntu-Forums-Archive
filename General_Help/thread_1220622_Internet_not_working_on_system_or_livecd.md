---
title: "Internet not working on system or livecd"
date: 2009-07-23
forum: General Help
---

### Post by akrchstn on 2009-07-23
Earlier today I edited my /etc/hosts and /etc/hostname files to change the name of my computer, re-booted and it all worked fine then later I booted into windows to play some games. When I started up ubuntu I tried to go to firefox and no pages would load and I couldn't install anything from my terminal. After a while of changing my system files back to what they were originally I deleted my ubuntu partion and tried to re-install. The livecd had no internet either but I just let that pass and installed but now my full install still has no internet. Everything works fine on windows though.

---

### Post by mthalis on 2009-07-23
Check you're network configuration.
> ifconfig 
post result.

---

### Post by akrchstn on 2009-07-23
```
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:85:ce:6f             inet addr:97.87.60.142  Bcast:97.87.63.255  Mask:255.255.252.0           inet6 addr: fe80::21b:b9ff:fe85:ce6f/64 Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:736 errors:0 dropped:0 overruns:0 frame:0           TX packets:30 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:48196 (48.1 KB)  TX bytes:4901 (4.9 KB)           Interrupt:252 Base address:0x6000   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by akrchstn on 2009-07-23
...bump

---

