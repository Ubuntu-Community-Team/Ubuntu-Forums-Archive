---
title: "Cannot connect to wired network (wireless works)"
date: 2010-09-17
forum: General Help
---

### Post by Lucky75 on 2010-09-17
Hi!

I rebooted my machine, and now I can't connect to the wired network for some reason. Wireless works fine.

```

eth0      Link encap:Ethernet  HWaddr 00:18:f3:5a:66:70  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:47:23:30  
          inet addr:192.168.11.140  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe47:2330/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40050278 (40.0 MB)  TX bytes:3536949 (3.5 MB)


```

If I try and manually ifup it, I get:
```
Ignoring unknown interface eth0=eth0.
```

Any suggestions? (10.04 gnome)

Thanks!

---

### Post by plucky on 2010-09-17
Open **System > Preferences > Network Connections** and under the "Wired Connection", Add a connection and under IPV4 settings make sure it is set to **Automatic DHCP**.

Then Apply new settings.

Good Luck

---

### Post by Lucky75 on 2010-09-17
Thanks, I'll give it a try. I don't see why it would have changed though.

---

### Post by Lucky75 on 2010-09-17
Yeah, I already have a connection. And I tried adding a new connection, still doesn't work though :(

Edit: Seems to work now, two reboots did the trick. Odd. Thanks? lol

---

### Post by plucky on 2010-09-18
> **Lucky75 said:**
> Yeah, I already have a connection. And I tried adding a new connection, still doesn't work though :(

Edit: Seems to work now, two reboots did the trick. Odd. Thanks? lol

If it is fixed,please use Thread Tools at top of page to mark as **[Solved]** 

Thank you.

---

### Post by dcstar on 2010-09-18
> **Lucky75 said:**
> Yeah, I already have a connection. And I tried adding a new connection, still doesn't work though :(

Edit: Seems to work now, two reboots did the trick. Odd. Thanks? lol

Sometimes hardware does not reset correctly after one reboot. If strange things like this happen again completely power off the machine (including disconnecting the power cable for about 30 seconds).

---

