---
title: "Configuring a network..."
date: 2006-05-05
forum: General Help
---

### Post by orlox on 2006-05-05
I need to configure the network on  a pc i'm using with xubuntu dapper. However, this distro doesn't seem to have a gui to do this like ubuntu, or kubuntu. I can't download anything, because i need to configure the network for that, so...does anyone now a solution on how to configure this? something terminal-based should be sufficient for the case...

---

### Post by pappo on 2006-05-05
All you should have to do is:

"sudo ifconfig eth0 192.X.X.X (whatever IP you want) netmask 255.255.255.0 up"

Then edit /etc/resolv.conf and put "nameserver X.X.X.X" where the X's are the IP address of your nameserver.  If you are on cable modem and have a router, the nameserver is usually  192.168.0.1

---

### Post by ScreemingBlue on 2006-05-05
Check what your nic is called by using the 'ifconfig' command and then edit the interfaces file by typing > sudo nano /etc/network/interfaces in a terminal window.
Mine looks like this 
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 10.0.0.10
	netmask 255.255.255.0
	network 10.0.0.0
	broadcast 10.0.0.255
	gateway 10.0.0.254
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 10.0.0.254

You may need to restart networking by typing > sudo /etc/init.d/networking restart

---

### Post by orlox on 2006-05-05
thanx!

---

