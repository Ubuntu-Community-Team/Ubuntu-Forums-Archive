---
title: "Can't setup bridge"
date: 2012-03-07
forum: General Help
---

### Post by diebodie on 2012-03-07
Trying to setup a bridge for my wireless network to output my Ethernet/internet to my ps3 (bought it refurbished for super cheap, it has no wifi... ehternet is the only way).  I'm folowing this guide if it helps you guys. [https://help.ubuntu.com/community/NetworkConnectionBridge]("https://help.ubuntu.com/community/NetworkConnectionBridge")


> Ryan-desktop ~ # ip addr flush dev eth0
Ryan-desktop ~ # ip addr flush dev wlan0
Ryan-desktop ~ # brctl addbr sexywow
Ryan-desktop ~ # brctl addif sexywow wlan0 eth0
>>can't add wlan0 to bridge sexywow: Operation not supported


Any ideas?

---

### Post by Habitual on 2012-03-07
```
ifconfig
```

output please. :)

---

### Post by diebodie on 2012-03-07
Ryan@ryan-desktop ~ $ ifconfig
e> th0      Link encap:Ethernet  HWaddr 00:13:8f:e7:b9:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1380 (1.3 KB)  TX bytes:1380 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:83:b1:b9  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:ad23:a7a6:1234:20f:b5ff:fe83:b1b9/64 Scope:Global
          inet6 addr: fe80::20f:b5ff:fe83:b1b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34438985 (34.4 MB)  TX bytes:5437706 (5.4 MB)

---

### Post by diebodie on 2012-03-08
I hate doing this, but I'm aching for some ps3 time....

Bumpity bump bump! :)

---

