---
title: "eth0 becomes eth2"
date: 2012-03-06
forum: General Help
---

### Post by MichaelGld on 2012-03-06
I upgraded from 10.04 to 11.04, and somehow my ethernet interface has changed from eth0 to eth2.  Can anyone tell me why? Is there a way to change it back?
```

michael@michael-desktop:~$ ifconfig -a
eth2      Link encap:Ethernet  HWaddr bc:5f:f4:19:70:08  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe19:7008/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9646142 (9.6 MB)  TX bytes:1959737 (1.9 MB)
          Interrupt:78 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11572 (11.5 KB)  TX bytes:11572 (11.5 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Bobhuber on 2012-03-06
> **MichaelGld said:**
> I upgraded from 10.04 to 11.04, and somehow my ethernet interface has changed from eth0 to eth2.  Can anyone tell me why? Is there a way to change it back?

Network card information (et0 - eth1)will be found in /etc/udev/rules.d/70-persitent-net.rules. If you change or add a different network card you will wind up with 2 entries in this file.The last entry if there are 2 will be your current card and should be NAME="eth0".
If not delete the first entry and change the second to etho.

---

