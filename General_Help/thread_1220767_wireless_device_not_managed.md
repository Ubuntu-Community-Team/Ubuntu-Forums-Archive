---
title: "wireless device not managed"
date: 2009-07-23
forum: General Help
---

### Post by _sluimers_ on 2009-07-23
I use [this USB adapter]("http://www.sitecom.com/product.php?productname=Wireless+Network+300N+USB+Adapter&productcode=WL-182&productid=579") for wifi.

I use mint version 7, freshly installed.
I use the latest RTA2870 RALINK driver, followed the driver installation instructions, which worked fine in the last version.

My problem is my nm-applet claims the device is not managed.

```

rogier@rogier-desktop ~/Desktop $ sudo /usr/lib/linuxmint/mintWifi/mintWifi.py
[sudo] password for rogier:
-------------------------
* I. scanning WIFI PCI devices...
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz 
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 00:1e:90:f3:eb:de 
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fef3:ebde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:837365 (837.3 KB)  TX bytes:152993 (152.9 KB)
          Interrupt:250

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

-------------------------
* V. querying DHCP...
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:00:00:00:00:00
Sending on   LPF/ra0/00:00:00:00:00:00
Listening on LPF/pan0/c6:25:f1:d4:50:33
Sending on   LPF/pan0/c6:25:f1:d4:50:33
Listening on LPF/eth0/00:1e:90:f3:eb:de
Sending on   LPF/eth0/00:1e:90:f3:eb:de
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
receive_packet failed on ra0: Network is down
DHCPOFFER of 192.168.1.33 from 192.168.1.254
DHCPREQUEST of 192.168.1.33 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.33 from 192.168.1.254
* Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.1.33 -- renewal in 11265 seconds.
-------------------------
* VI. querying nslookup google.com...
Server:      192.168.1.254
Address:   192.168.1.254#53

Non-authoritative answer:
Name:   google.com
Address: 74.125.45.100
Name:   google.com
Address: 74.125.67.100
Name:   google.com
Address: 74.125.127.100

rogier@rogier-desktop ~/Desktop $ 

```

---

