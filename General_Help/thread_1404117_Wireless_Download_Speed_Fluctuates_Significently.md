---
title: "Wireless Download Speed Fluctuates Significently"
date: 2010-02-11
forum: General Help
---

### Post by mattsweegold on 2010-02-11
[FONT=Times New Roman][SIZE=3]      On my wireless network, the computer directly connected to the modem remains unaffected at all times of the day. This computer maintains a download speed of about 18000 kbps and uses a wrt54g linksys router. However, the computer upstairs which uses wmp54g adapter fluctuates between 14000 kbps to about 500kpbs at different intervals throughout the day[SIZE=2]. [/SIZE][/SIZE][/FONT][SIZE=3][FONT=Times New Roman][SIZE=3]My ifconfig is as following[/SIZE][/FONT][SIZE=3]:[/SIZE] [SIZE=2]

eth0      Link encap:Ethernet  HWaddr 00:15:f2:4b:c7:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1784 (1.7 KB)  TX bytes:1784 (1.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:8c:28:f3  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24673893 (24.6 MB)  TX bytes:6587464 (6.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-8C-28-F3-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/SIZE]

[/SIZE]

---

### Post by shriramrs31 on 2010-02-11
It doesn't seem like a driver problem (unless you have a better signal strength in some other ditro or Operating System).

It can be most probably due to interference. Try other channels. you must be able to find one that is pretty stable.

Or probably because of the distance, the signal strength is less. In any case trying out different channels might give you some advantage.

You can also try making DIY direction specific antenna for your WLAN router, to strengthen the signal in a particular direction.

---

### Post by mattsweegold on 2010-02-11
Thank you I am going to change the channels.

---

