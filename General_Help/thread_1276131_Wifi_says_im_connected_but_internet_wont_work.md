---
title: "Wifi says im connected but internet wont work"
date: 2009-09-26
forum: General Help
---

### Post by xxhopingtearsxx on 2009-09-26
I have Ubuntu 9.04..

Yesterday, out of no where, a day after I found a good theme and iconset that makes switching to Ubuntu easier.. my wireless acts up. I'm pretty sure it's not the theme's fault, so don't start assuming that. I installed some new updates, so that's something that I'm thinking about that could've caused it, but I doubt it..

My top panel says I am connected to the internet. I go into Firefox after starting up Ubuntu, and load google. It loads. I refresh, and it attempts to load but it doesn't.. Usually, when I start Ubuntu, I would use the internet for a while.. get disconnected, wait for it to reconnect, and when it's done there's no more problems until I start Ubuntu again and it does the same thing again. Since I thought it was the usual thing, I just waited to get disconnected and connected. It happened, I went into google, but it wouldn't load.

I'm pretty frustrated, since I really don't feel like using Windows at all, but it's the only thing I can do since my wireless won't work well. What can I do? I have a realtek rtl8187b wifi and Toshiba Satellite L305-S5955.

Please respond fast. I'll take any suggestions. I really want this fixed..

---

### Post by TheLions on 2009-09-26
is your router connected to Internet? It seem that you are connected to router, but router is disconnected.

---

### Post by ww711 on 2009-09-26
What do you get when you type in a terminal?

```
ifconfig -a
```

---

### Post by helenawahlberg on 2010-11-17
right now I'm connected to the internet and everything is fine but sometimes I have the exact same problem as the person about. Right now ifconfig -a gives me this


eth0      Link encap:Ethernet  HWaddr 00:24:8c:74:b0:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:12:3f:fc  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe12:3ffc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16451 errors:18 dropped:17490 overruns:0 frame:0
          TX packets:17546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13958763 (13.9 MB)  TX bytes:3674074 (3.6 MB)
          Interrupt:18 Memory:e1228000-e1228100

---

### Post by tad1073 on 2010-11-17
When stuff like that happens the first thing you should do is unplug the router from the wall socket for about 30 seconds then plug it back in. That has worked for me numerous times.

---

