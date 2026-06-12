---
title: "No Net Connection"
date: 2011-06-18
forum: General Help
---

### Post by BerneGPG on 2011-06-18
Hi,
Using 11.04 what programme do i run to troubleshoot my net connection as its currently down?


berneGPG

---

### Post by crispy_420 on 2011-06-18
ifconfig should be a decent starting point. You can then see if you have a valid IP and subnet.

---

### Post by BerneGPG on 2011-06-21
Hi,
Being nearly new to 11.04 I entered ipconifg into the Terminal but nothing was found, I suspect you intended me to enter the command elsewhere sorry Im unsure.  Anyhow whatever happened, yet again, Ubuntu has solved by its own diagnostic, any previous connection issue and now  11.04 is now getting me online without any difficulty.

For the record though what programe were you suggesting I enter the ipconfig into?

Thank you for the reply,

berneGPG

---

### Post by grahammechanical on 2011-06-21
This link to the trouble shooting guide will help if the problem re-occurs

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

The terminal was the correct place for that command but it is ifconfig not ipconfig as you typed in your reply. Unless of course the letter p is a typing error in the reply.

This is what I get when I type ifconfig in the terminal

> eth0      Link encap:Ethernet  HWaddr 00:1a:92:82:db:59  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe82:db59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74738065 (74.7 MB)  TX bytes:3552935 (3.5 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:82:d4:32  
          inet6 addr: fe80::21a:92ff:fe82:d432/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:0e:9b:e0  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe0e:9be0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:456145 (456.1 KB)  TX bytes:4230 (4.2 KB)
I am connected by both a wireless adapter (wlan0) and one ethernet adapter (eth0). I also have another ethernet adapter (eth1). Notice that all three are UP and also RUNNING. If that is not showing then you do not have a working network adapter. Can you see what is different about eth1 when compared to eth0 and wlan0? Both eth0 and wlan0 have an inet addr: address which is my router/modem. Whereas, eth1 does not have inet addr:  Therefore, eth1 is not connected to the router.

Regards.

---

