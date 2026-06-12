---
title: "eth0 to ra0"
date: 2006-03-20
forum: General Help
---

### Post by Linkhiei on 2006-03-20
Could anyone tell me how to change ur default network interface from eth0 to ra0 in a text terminal mode? Any help is appreciated :)

---

### Post by cilynx on 2006-03-20
/etc/network/interfaces is your friend

"man interfaces"

---

### Post by Linkhiei on 2006-03-20
I tried editing that, maybe I did something wrong. What would I need to change in it?

My current interfaces file looks like so:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface ra0 inet DHCP

---

