---
title: "network interface configuration on an ubuntu server + desktop"
date: 2010-01-12
forum: General Help
---

### Post by mansonthomas on 2010-01-12
Hi,

  I've got a server that was installed with ubuntu server, on which I've added the desktop functionality (to use XBMC).

  From that day, I've a strange behavior on my network configuration which was initially set manually in /etc/network/interfaces (192.168.0.1)

  In the Gnome interface, in the "network connections" eth0 is set in DHCP, so instead of my static network config I've a DHCP one (which mess up many things) (192.168.0.11)

If I try to bring down and up the eth0 network interface I get some errors but the ip of eth0 is set back to the manual config (192.168.0.1)


[PHP]thomas@home:/etc/network/if-up.d$ sudo ifdown eth0
ifdown: interface eth0 not configured
thomas@home:/etc/network/if-up.d$ sudo ifup eth0
SIOCADDRT: File exists
Failed to bring up eth0.[/PHP]

I'd rather use the /etc/network/interfaces config file instead of the graphical one, or I need to know where on the filesystem it's stored and How can I interract with my eth0 network card (bring up/down) because I mainly access my server remotely (ssh)

Thanks for help,
Thomas.

Extra question : How do I set the background color in terminator ? If I do right click, edit profile, I've a message that tells the change will not be saved, see terminator_config manpage, when I try the solution described there it doesn't work. (I've set a config file here: ~/.config/terminator/config and $XDG_CONFIG_HOME is not set)

---

### Post by gsmanners on 2010-01-12
If you use static IP, you don't need network-manager at all. Feel free to remove it.

To reconfigure your network, change the /etc/network/intefaces as desired, then do the following:

```
sudo /etc/init.d/networking restart
```

/etc/network/interfaces should contain something like:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address 192.168.0.1
  netmask 255.255.255.0
  gateway 192.168.1.1
```

The above assumes you're connected to a router at 192.168.1.1.

---

