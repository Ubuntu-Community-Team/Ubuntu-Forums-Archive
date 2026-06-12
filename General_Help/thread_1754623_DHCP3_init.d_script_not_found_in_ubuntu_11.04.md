---
title: "DHCP3 init.d script not found in ubuntu 11.04"
date: 2011-05-10
forum: General Help
---

### Post by reza.adinata on 2011-05-10
Hi all,

This is kinda strange, i just installed dhcp3-server in ubuntu 11.04 , but when I try to find the starting script in /etc/init.d/dchp3-server start, it states 

bash: /etc/init.d/dhcp3-server: No such file or directory

I have installed the dhcp3-server,howcome there is no script for executing dhcp server? 

Please kindly help

---

### Post by DaithiF on 2011-05-10
Hi, I believe it is /etc/init.d/isc-dhcp-server
dhcp3-server is a dummy package which wraps the real isc-dhcp-server package

---

### Post by reza.adinata on 2011-05-10
Wow.. that is interesting, because most tutorials point to init.d/dchp3-server .

Thank you!

---

### Post by uniomni on 2011-08-31
Does that mean that the old configuration file /etc/dhcp3/dhcp.conf has moved too?
I have just upgraded from 9.04 to 11.04 and I get error of the following form when trying to do /etc/init.d/isc-dhcp-server start

Aug 31 10:53:06 alamba dhcpd: No subnet declaration for eth1 (192.168.11.10).
Aug 31 10:53:06 alamba dhcpd: ** Ignoring requests on eth1.  If this is not what
Aug 31 10:53:06 alamba dhcpd:    you want, please write a subnet declaration
Aug 31 10:53:06 alamba dhcpd:    in your dhcpd.conf file for the network segment
Aug 31 10:53:06 alamba dhcpd:    to which interface eth1 is attached. **

needless to say ifconfig eth1 shows that it should be OK

root@alamba:/etc/init.d# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:25:b3:25:b1:f8  
          inet addr:192.168.11.10  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::225:b3ff:fe25:b1f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23909097 (23.9 MB)  TX bytes:12462757 (12.4 MB)
          Interrupt:17 Memory:f2000000-f2012800 


I noticed that the startup script /etc/init.d/isc-dhcp-server script points to /etc/dhcp and not /etc/dhcp3:
# Default config file
CONFIG_FILE=/etc/dhcp/dhcpd.conf

but I am at a loss what exactly I should do.
Many thanks
Ole

---

### Post by WhiteHorse on 2011-09-01
This isn't solved. The /etc/init.d/isc-dhcp-server script looks for /etc/defaults/isc-dhcp-server rather than /etc/defaults/dhcp3-server which makes all the prior tutorials defective without this knowledge.

---

### Post by Efaustus9 on 2011-11-20
I am using ubuntu 11.10 and I was following this tutorial 

[https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3](https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3)

it was working fine until I get to the step

/etc/init.d/dhcp3-server start

after entering the command I get the response

 No such file or directory

any solutions?

---

### Post by wlraider70 on 2012-04-21
try

sudo /etc/init.d/isc-dhcp-server start

---

