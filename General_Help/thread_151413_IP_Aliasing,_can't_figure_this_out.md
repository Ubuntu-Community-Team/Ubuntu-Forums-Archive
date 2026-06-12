---
title: "IP Aliasing, can't figure this out"
date: 2006-03-27
forum: General Help
---

### Post by DjKritical on 2006-03-27
Heya,

Here's what I've done to my /etc/network/interfaces

```

# This file describes the network interfaces available on your system
and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
	address 10.10.10.2
	netmask 255.255.255.0
	network 10.10.10.0
	broadcast 10.10.10.255
	gateway 10.10.10.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 10.10.10.1

iface eth0:1 inet static
	address 10.10.10.50
	netmask 255.255.255.0


auto eth0

```

When I type **sudo invoke-rc.d restart networking**

I get **Reconfiguring Network Interfaces - [COLOR="Red"]Fail[/COLOR]**

I don't even know where to find the logs? :-k 

Cheers :D

---

### Post by DjKritical on 2006-03-27
I tried restarting.. now the machine wont boot.. I was administoring it remotely... help!! :(

---

### Post by dcstar on 2006-03-28
[QUOTE=DjKritical]I tried restarting.. now the machine wont boot.. I was administoring it remotely... help!! :([/QUOTE]
Logs are in /var/logs.

If you have stuffed up the network interface, then you won't get any further remote access.

This may be of assistance:

[http://www.faqs.org/docs/Linux-mini/IP-Alias.html](http://www.faqs.org/docs/Linux-mini/IP-Alias.html)

---

