---
title: "no wired network connection error"
date: 2011-04-30
forum: General Help
---

### Post by creatxr on 2011-04-30
it worked before i went to bed yesterday.
but, this morning, i power on my computer, it is no wired network connections.
i tried command ifconfig and lshw -c network . it could find the network card eth0.

> lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 03
       serial: 00:1f:bc:08:cf:92
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:30 ioport:ce00(size=256) memory:f3bff000-f3bfffff(prefetchable) memory:f3bf8000-f3bfbfff(prefetchable) memory:f3ce0000-f3cfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:78:72:58:d1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.55 multicast=yes wireless=IEEE 802.11bg



> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:bc:08:cf:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8112 (8.1 KB)  TX bytes:8112 (8.1 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.113.1  Bcast:172.16.113.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.241.1  Bcast:192.168.241.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:78:72:58:d1  
          inet addr:192.168.1.55  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe72:58d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4308067 (4.3 MB)  TX bytes:1035874 (1.0 MB)


---

### Post by yossell on 2011-04-30
There's been an issue with BT home-hubs suddenly not working with Ubuntu after a firmware upgrade. I seemed to get mine going again by manually filling in DHCP information.

[http://ubuntuforums.org/showthread.php?t=1736079](http://ubuntuforums.org/showthread.php?t=1736079)

[http://ubuntuforums.org/showthread.php?t=1737366](http://ubuntuforums.org/showthread.php?t=1737366)

---

### Post by creatxr on 2011-04-30
i've set a static ip for eth0. but, as you see, it has not a ip with eth0.
i don't know what happened. so i format drive and upgrade to ver 11.04. 
it has still the same problem.
i am puzzled , it's a software problem or a hardware problem?

---

### Post by crimton on 2011-04-30
i am having similar problems. i was on 10.10 yesterday and all was fine. i did a fresh install of 11.04 and now i have wireless but no wired.

---

