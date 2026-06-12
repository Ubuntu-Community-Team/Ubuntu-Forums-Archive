---
title: "Rookie having trouble installing Ndiswrapper 1.56 to have wireless intternet"
date: 2011-04-23
forum: General Help
---

### Post by armadi on 2011-04-23
I've been having problems installing this and so far I've managed to install the drivers but I can't get internet to work properly.

this is what I get in the terminal(I'm still new with so I don't really understand what I have to do to fix it):

armadi@ubuntu:~$ sudo ifdown wlan0
[sudo] password for armadi: 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1469
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:18:e7:45:70:0f
Sending on   LPF/wlan0/00:18:e7:45:70:0f
Sending on   Socket/fallback
grep: /etc/resolv.conf: No such file or directory
armadi@ubuntu:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:18:e7:45:70:0f
Sending on   LPF/wlan0/00:18:e7:45:70:0f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
armadi@ubuntu:~$ 





armadi@ubuntu:~$      iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

armadi@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:87:83:f4:f2  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52976 (52.9 KB)  TX bytes:52976 (52.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:e7:45:70:0f  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:18:e7:45:70:0f  
          inet addr:169.254.5.193  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

armadi@ubuntu:~$ 



Thanks for any hint you can give me.

---

