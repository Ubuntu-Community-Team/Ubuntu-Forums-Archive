---
title: "Gateway Problem"
date: 2009-09-25
forum: General Help
---

### Post by mikehenson on 2009-09-25
System Configuration:
Two Dual boot computers Windows XP and Ubuntu 9.04

Symptoms:
Ubuntu gets valid IP from DHCP.
Ubuntu can browse local computers and network drives.
Ubuntu can not browse the web.
Ubuntu can only ping computers in local network.
Ubuntu Default gateway 10.0.0.2
Windows has no issues.
Windows gets valid IP from DHCP
Windows can browse local computers and network drives.
Windows can browse the web. 
Windows Default gateway 10.0.0.2


Solution:
Windows would time out when tracert [www.google.com](www.google.com) (start run cmd then type  tracert [www.google.com](www.google.com) ) Then Windows would go out through 10.0.0.1. 
Ubuntu never went out 10.0.0.1 and just waited for ever to time out.
In terminal run 
```
route
```
It will print out a table like this one:
```

Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
10.0.0.0        *               255.255.255.0   U     1      0        0 eth0 
link-local      *               255.255.0.0     U     1000   0        0 eth0 
default         10.0.0.2        0.0.0.0         UG    0      0        0 eth0 

```
Then run
```

sudo route del default gw 10.0.0.2
sudo route add default gw 10.0.0.1  

```

This solved the problem. Ubuntu needed the correct default route.

---

### Post by VipX1 on 2009-09-25
> **mikehenson said:**
> System Configuration:

Symptoms:
Ubuntu gets valid IP from DHCP.
Ubuntu can browse local computers and network drives.
Ubuntu can not browse the web.
Ubuntu can only ping computers in local network.
Ubuntu Default gateway 10.0.0.2
Windows has no issues.
Windows gets valid IP from DHCP
Windows can browse local computers and network drives.
Windows can browse the web. 
Windows Default gateway 10.0.0.2

Then run
```

sudo route del default gw 10.0.0.2
sudo route add default gw 10.0.0.1  

```This solved the problem. Ubuntu needed the correct default route.

So now Ubuntu has default Gate 10.0.0.1 as a result of the "route add" command and Windows still has 10.0.0.2 as listed above, am I understanding right? 
Default gate is always the i.p. address of the device you are using for the internet connection.(In this case your router) If you don't enter the default gate address you can only see other computers that are in the same subnet mask as you   on the LAN. You will have no router to route you threw to other networks. i.e. The WAN!
```
/etc/resolv.conf
```Another handy file..

---

### Post by mikehenson on 2009-09-29
> **VipX1 said:**
> So now Ubuntu has default Gate 10.0.0.1 as a result of the "route add" command and Windows still has 10.0.0.2 as listed above, am I understanding right? 

Yes, until I changed the default gateway in Windows. I don't know why but Windows would find the way out after timing out on 10.0.0.2. The timing out caused Firefox to pause for a second before loading a web page.

---

