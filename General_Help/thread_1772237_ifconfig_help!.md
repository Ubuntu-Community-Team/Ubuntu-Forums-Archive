---
title: "ifconfig help!"
date: 2011-05-31
forum: General Help
---

### Post by wambo on 2011-05-31
Hi,
 
When doing the ifconfig command I only receive the IPV6 address.
 
How do I specify that I need the IPV4 address???

---

### Post by janpol on 2011-05-31
You want to config a static ip using the terminal? If so just use the following commands:

> sudo ifconfig [iface] [ip] netmask [mask]

Where:

[iface]: The interface you are configuring 
[ip]: The ip address
[mask]: The netmask

For example:

> sudo ifconfig eth0 192.168.0.1 netmask 255.255.255.0

After that, if the interface is down, bring the interface up with:

> sudo ifconfig eth0 up

On the other hand, if you want to explicitly tell your PC to get an IP address from a DHCP server, you can run the following command:

> sudo dhclient

PS: All this can also be accomplished using the Graphical Interface in a much easier way via the "Network Connections" tool ;)

---

### Post by sanderj on 2011-05-31
> **wambo said:**
> Hi,
 
When doing the ifconfig command I only receive the IPV6 address.
 
How do I specify that I need the IPV4 address???

The IPv6 address: does it start with fe80:: ? If so, it's just an internal IPv6 address.

Is there any LAN / Internet connectivity at all? 

Probably best to post the output of ifconfig here. My guess is you have no LAN / Internet access at all, and that ifconfig is just reporting that.

HTH

---

### Post by wambo on 2011-06-01
I've resolved this by manually setting the IP.
 
And I can't use the graphical interface as its Ubuntu Server :P

---

