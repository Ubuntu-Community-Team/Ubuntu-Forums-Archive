---
title: "Problem assigning Gateway"
date: 2006-03-31
forum: General Help
---

### Post by thegrifman on 2006-03-31
I just installed Ubuntu on my tower and am having trouble getting out to the net.  I can communicate with other machines on my network fine and it seems to be a gateway problem. Below are my /etc/network/interfaces file and the output of "route -n".  I've also attached screenshots of how I configured it in the connection properties applet for gnome.  I'm pretty sure that I need to get the gateway in my route from line 2 up to line 1, but can't quite seem to figure out how to do that.  Any help would be greatly appreciated.

Output of "route -n":
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

```

My /etc/network/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1

auto eth1
```

---

### Post by Ramses de Norre on 2006-03-31
man route may help you, though I don't really understand how it all works myself ;)

---

### Post by thegrifman on 2006-03-31
Yeah, I tried that but couldn't really figure out how to modify a route versus add or delete.

---

### Post by xenmax on 2006-03-31
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```
This is output of my "route -n" which seems very similar to yours, but i am on the net right now!

---

