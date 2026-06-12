---
title: "2 network interfaces config"
date: 2011-09-08
forum: General Help
---

### Post by egrimisu on 2011-09-08
Hi,

i have 2 interfaces on my ubuntu,
the /etc/network/interfaces is set as folowing:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
	address 192.168.2.11
	netmask 255.255.255.0
	network 192.168.2.0
	broadcast 192.168.2.255
	gateway 192.168.2.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.2.10
	dns-search my.local

auto eth0

the second interface is used as a wan for a client pc( secondary net server) in the vmware server v2 that is installed on the box. 

The wan works fine for the net server
on the ubuntu box web is browsable, no dns errors
The problem - i can't ping any local pc machine using host names

for the wan to work i had to edit that wired connection and to the ipv4 settings i checked Method - Link local only. I believe i  haven't made the right settings here and in /etc/network/interfaces

Please help.

---

