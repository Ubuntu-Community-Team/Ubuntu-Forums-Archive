---
title: "the internet doesn't seem to function, except in liveCD"
date: 2006-06-21
forum: General Help
---

### Post by ImplicitProcrastination on 2006-06-21
Hi everybody, here's my situation:

Ubuntu always serves me well in college.

Unfortunately I find myself back at my uncles using his cable connection, which he accesses through a wireless router which has never worked for me.

However with some tweaking (can't remember what I did, it took hours of toying) I got 5.10 to work here through the router corded (so the Windows people can have their wireless, bah).

Anyway time came to pass, I missed certain games and installed windows over it figuring that I had done messed that setup up anyway, I'd just dual-boot Dapper.

I find myself in the position of the internet just plain not working through this setup. I tried installing using the alternate CD and it gave me a warning that security.ubuntu.com couldn't be found.  Couldn't even check the basic repositories after installing it through the liveCD.

As a matter of fact the only internet I could get working was when I'm running from the liveCD without having installed Ubuntu (which I am doing now).

Here's a random command if you guys can think of more stuff for me to type so you can interprit and explain the results and maybe I'll learn and get this problem solved that would be great:

dhclient:
```
ubuntu@ubuntu:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:90:96:c5:b1:9c
Sending on   LPF/ath0/00:90:96:c5:b1:9c
Listening on LPF/eth0/00:02:3f:d6:7e:d3
Sending on   LPF/eth0/00:02:3f:d6:7e:d3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.5 -- renewal in 36294 seconds.
ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

```

ifconfig:
```
ubuntu@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:90:96:C5:B1:9C
          inet6 addr: fe80::290:96ff:fec5:b19c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Memory:dcb80000-dcb90000

eth0      Link encap:Ethernet  HWaddr 00:02:3F:D6:7E:D3
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fed6:7ed3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18950190 (18.0 MiB)  TX bytes:759361 (741.5 KiB)
          Interrupt:201 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

```

route:

```
ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         BWA711          0.0.0.0         UG    0      0        0 eth0

```


Thanks in advance, Ian.

---

### Post by unf on 2006-06-21
lspci | grep Ethernet
lsmod

paste here

---

### Post by ImplicitProcrastination on 2006-06-21
I'll be damned it worked.



I apologize for wasting your time dude, I've been at this all night. I will immediately hit this post back up should the problems rematerialize cause I'm not really all that sure what I did differently.

---

