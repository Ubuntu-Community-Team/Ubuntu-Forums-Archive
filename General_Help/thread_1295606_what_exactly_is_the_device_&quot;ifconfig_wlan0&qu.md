---
title: "what exactly is the device &quot;ifconfig wlan0&quot; refers to?"
date: 2009-10-19
forum: General Help
---

### Post by bodyharvester on 2009-10-19
when i type

```
sudo ifconfig wlan0
```i get this

```
wlan0: error fetching interface information: Device not found
```can anyone tell me exactly what this statement means? i got the same output from using the live cd of 9.04. is it hardware related?

---

### Post by mcduck on 2009-10-19
wlan0 would be a wireless network card. But you should note that depending on your network card it might actually be called as eth* or ra* or something else instead.

Anyway, the error is telling you thet there is no such device as "wlan0" on your system.

Try running "sudo ifconfig -a" to list all your network interfaces.

---

### Post by bodyharvester on 2009-10-19
i see, thanks.

after running that command you suggested "wlan0" is not listed, its a little embarassing that ive been thinking that was the problem for so long

```
eth0      Link encap:Ethernet  HWaddr 00:21:70:c1:fb:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

eth1      Link encap:Ethernet  HWaddr 00:23:08:1f:63:95  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:221
          TX packets:38 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1106 (1.1 KB)  TX bytes:5549 (5.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1088 (1.0 KB)  TX bytes:1088 (1.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.46.15.190  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64215 (64.2 KB)  TX bytes:45756 (45.7 KB)
```

which one of these could be causing my problem ([http://ubuntuforums.org/showthread.php?t=1295248)?](http://ubuntuforums.org/showthread.php?t=1295248)?) i can connect to a wireless network but there is no network traffic and i cant surf the net or anything. its really annoying, i cant watch anime continuously

---

