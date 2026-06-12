---
title: "Network Disabled mac address 00:00:00:00:00:00"
date: 2012-05-02
forum: General Help
---

### Post by fetofa on 2012-05-02
I am running a xen guest machine with a ubuntu 12.04 OS.

The problem I am havin is that I cant get internet on that virtual machine. The configuration for the other virtual machine is the same (other linux OS) and they have internet.
Some information:

ftorres@BBB:~$ ifconfig eth0
eth0   link encap:Ethernet HWaddr 00:00:00:00:00:00
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

ftorres@BBB:~$ sudo lshw -C network
*-network DISABLED
   description: Ethernet interface
   physical id: 1
   logical name eth0
   capabilities: ethernet physical
   configuration: broadcast=yes driver=vif link=no multicast=yes

ftorres@BBB:~$ cat /ect/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


ftorres@BBB:~$ sudo /etc/init.d/networking restart
*Running /etc/init.d/networking restart is deprecated because it may not be enable again some interfaces
*Reconfiguring network interfaces...
RTNETLINK answers: Cannot assign requested address
Failed to bring up eth0                                                                                                           [ ok ]

---

### Post by tmfries on 2013-01-10
you find an answer to this?

---

