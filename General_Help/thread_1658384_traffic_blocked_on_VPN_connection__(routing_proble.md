---
title: "traffic blocked on VPN connection  (routing problem?)"
date: 2011-01-02
forum: General Help
---

### Post by GGabor74 on 2011-01-02
Hello!

I'm trying to connect to the [www.freeopenvpn.com]("http://www.freeopenvpn.com") vpn service from my ubuntu 10.04 netbook edition. Installed the parts based on the instruction of the website, then the connection successful (lock icon on the connection area)  but.....

the traffic does not go through, ping rejects with some "buffer error", network monitor does not show any data flow on the lan card. after the connection. Was trying it from commandline, and from gui as well. Same result. Can't even navigate to the service start page.

I do not have firewall, using the linksys built in firewall in my router. The same (dual boot) machine and router let the same vpn work under win XP, so the hardware is fine.

I suspect that it is a routing problem. (using dhcp from the modem-router)

  Found that the vpn module installed the virtual tun0 interface and set up the routing table automatically.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
  173.192.86.142  192.168.1.1     255.255.255.255 UGH       0 0          0 eth0
  192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
  link-local      *               255.255.0.0     U         0 0          0 eth0
  10.60.0.0       *               255.255.0.0     U         0 0          0 tun0
  default         10.60.0.1       0.0.0.0         UG        0 0          0 tun0
```Where the 173... is the vpn server, the 192.168.1.1 is my router, the 10.60.... is the vpn channel given ip address range

  also the tun0 drops each package

```

  ifconfig tun0
  tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
            inet addr:10.60.0.6  P-t-P:10.60.0.6  Mask:255.255.0.0
            UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
            RX packets:1 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:564 overruns:0 carrier:0
            collisions:0 txqueuelen:100 
            RX bytes:28 (28.0 B) TX bytes:0 (0.0 B)

```I tried to change the routing table, but I could not, and surprisingly .... after connecting to the vpn, the routing table resets to the above state :confused:

what I tried is to remove the last row and add a new default gateway. However it failed.

```

  route del -net 0.0.0.0 netmask 0.0.0.0 gw 10.60.0.1 metric 0 dev tun0
  route add -net default netmask 0.0.0.0 gw 192.168.1.1 metric 0 dev tun0
SIOCADDRT: No such process

```I'm hopeless at this point, can anyone help me out? What is the cause of this "traffic blocked" poblem? How your routing table looks like when connecting to this service?

Thanks
Gabor

---

### Post by GGabor74 on 2011-01-06
solved:

found a TCP type openvpn provider which works fine when connecting from the Network Manager

---

