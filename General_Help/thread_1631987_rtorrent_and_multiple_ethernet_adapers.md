---
title: "rtorrent and multiple ethernet adapers?"
date: 2010-11-27
forum: General Help
---

### Post by sr_guy on 2010-11-27
I have two NIC cards installed in my ubuntu box. Is there a way to control which NIC interface rtorrent uses in its config? 

```

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:67ff:fe6c:af83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:204093 (204.0 KB)  TX bytes:1212387 (1.2 MB)
          Interrupt:27 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.69.129  Bcast:192.168.69.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe06:1f4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4206 (4.2 KB)  TX bytes:11578 (11.5 KB)
          Interrupt:16 Base address:0xbc00



```

---

