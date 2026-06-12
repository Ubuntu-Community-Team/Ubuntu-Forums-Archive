---
title: "firewall"
date: 2010-06-06
forum: General Help
---

### Post by sunflowers on 2010-06-06
Hi.
is there any firewall program on kubuntu to show me how much of packets I have downloaded or sent ?
it means, how can I know how much of traffic I have used?
Thank you.

---

### Post by Leppie on 2010-06-06
ifconfig can show you this information:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx 
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe1e:21dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          [COLOR=Red]RX bytes:79989771 (79.9 MB)  TX bytes:12771768 (12.7 MB)[/COLOR]

```

---

