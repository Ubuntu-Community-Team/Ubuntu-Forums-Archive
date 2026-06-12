---
title: "Slow wired Internet with 11.04 64-bit"
date: 2012-05-19
forum: General Help
---

### Post by MichaelGld on 2012-05-19
I have just noticed a massive slowdown in my Internet speeds (both up and down) under Ubuntu as compared to under Windows 7.  (I am dual-booting.)

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

        at speedtest.net

Windows                    31.26 Mbps  down   11.65 Mbps up      23 ms ping
Ubuntu               2.84 down                            0.08 up          19 ping

        at Bandwithplace

Windows                       24.18 down                  14.68 up
Ubuntu                   2.24 down                        84k up
  
ifconfig -a -v
```
 eth0      Link encap:Ethernet  HWaddr 00:25:22:dd:74:e4  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:fedd:74e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51497 errors:0 dropped:51497 overruns:0 frame:51497
          TX packets:46264 errors:0 dropped:297 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59070231 (59.0 MB)  TX bytes:11151374 (11.1 MB)
          Interrupt:72 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:339516 (339.5 KB)  TX bytes:339516 (339.5 KB)


```

I would appreciate any help.

---

