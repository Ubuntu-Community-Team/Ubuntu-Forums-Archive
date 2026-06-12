---
title: "Unstable wired connection Ubuntu 11.10"
date: 2012-02-06
forum: General Help
---

### Post by Soif on 2012-02-06
Hello!

I installed Ubuntu 11.10 64-bit yesterday and everything worked fine until I used my internet connection.

It's very unstable, sometimes it works fine but most of the time it takes forever for a website to load. Or when I'm on skype, I don't hear everything my friends say.
I have no problem at all on Windows 7 64-bit and my speed is about 20 times higher.

I already disabled IPv6, updated my Realtek drivers, changed the order in nsswitch.conf, changed the MTU value to 1492 and a few more things I don't remember.

Can someone help me to fix it, please?

Thanks!

```
eth0      Link encap:Ethernet  HWaddr f4:6d:04:53:ba:2c  
          inet addr:192.168.0.143  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:14848 errors:0 dropped:14848 overruns:0 frame:14848
          TX packets:15260 errors:0 dropped:266 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13729713 (13.7 MB)  TX bytes:2099950 (2.0 MB)
          Interrupt:48 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54859 (54.8 KB)  TX bytes:54859 (54.8 KB)

```

---

