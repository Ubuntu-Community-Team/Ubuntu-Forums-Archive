---
title: "vpnc routing : Operation not permitted"
date: 2006-02-16
forum: General Help
---

### Post by colokevin on 2006-02-16
I'm trying to connect to a Cisco VPN using vpnc version 0.3.3.  Everything looks fine during authentication and connection establishment, but after that my connectivity is non-existant.  No DNS, and can only ping the two routes I have in my routing table.  When I try to ping something else (google), I get:

PING 72.14.203.104 (72.14.203.104) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

I searched the forums and saw a few people have posted this problem, but I haven't found any solutions.

Any help is appreciated.  Thank you.

---

### Post by schilcha on 2006-02-16
double post -- removed

---

### Post by schilcha on 2006-02-16
I'm using vpnc 0.3.3-0ubuntu2 -- so don't loose your faith in vpnc!

[QUOTE=colokevin]I'm trying to connect to a Cisco VPN using vpnc version 0.3.3.  Everything looks fine during authentication and connection establishment, but after that my connectivity is non-existant.[/QUOTE]

Are you sure, the connection is there? After I connect to the VPN, I have the following interface set up (use the command ifconfig to generate this list):
> 
tun0 Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
     inet addr:10.11.12.13  P-t-P:10.11.12.13  Mask:255.255.255.255
     UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:500
     RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I'm pretty confident, you've already checked this -- it's just to make sure...

[QUOTE=colokevin]No DNS, and can only ping the two routes I have in my routing table.  When I try to ping something else (google), I get:

PING 72.14.203.104 (72.14.203.104) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
[/QUOTE]
I've seen error "Operation not permitted" only on ping's that were explicitly denied by a firewall (iptables, but I don't know if that matters...)

I also had (and partially still have) serious problems with firewalls/routers. Are you behind a router / a firewall?

I'm using vpnc in its (more or less) default setting. The connection is set up such that _any_ traffic is sent througe the vpn-connection.
Therefore, my routing-table has the following entry (check "route -n")
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[...]
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0


Furthermore, /etc/resolv.conf is automagically modified to use other name-servers.

Are you sure that this behaviour is ok for you? Do you have to use some different dns-server? Do you really want to send all your traffic through the vpn? Is routing and nameserver-information updated correctly?

---

### Post by colokevin on 2006-02-16
My ifconfig looks very similar to yours.

I've been using Firestarter to open ports.  I'm also behind a router.  I install the Windows vpn client on a different machine behind the same router, and connect without a problem.

---

### Post by schilcha on 2006-02-17
[QUOTE=colokevin]I've been using Firestarter to open ports.[/QUOTE]

Can you try to disable Firestarter and try to connect then?

I've never used firestarter and my experience with iptables is moderate. But I know, you need to allow traffic at port 500 (I guess udp and tcp) and traffic via the esp-protocol to make the vpn-connection work.

Also you need to take care of the new interface (tun0). If your default policy is DENY, this might also apply to the vpn-interface -- that'd explain the ping-error. You probably need to define firewall-rules for tun0 as well. Have a look at the logs, if vpn-packages are dropped by the firewall.

Good Luck!

---

### Post by hajk on 2006-02-17
Have a look at [http://www.ces.clemson.edu/linux/nm.shtml](http://www.ces.clemson.edu/linux/nm.shtml) under Configuration of Firestarter.

---

### Post by colokevin on 2006-02-17
Well, it's definitely a firewall issue.  I disabled Firestarter completely, and I connect to the VPN and function without a problem.  I suppose I don't even really need a software firewall seeing as how I'm behind a router w/ a firewall.

Thanks for your help everyone!

---

