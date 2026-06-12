---
title: "Startup script"
date: 2012-08-27
forum: General Help
---

### Post by marlow59 on 2012-08-27
What can I do to make a script that needs root privilege run on startup ? (typically, the an iptables script).
Thanks for your answers.

---

### Post by Doug S on 2012-08-27
There are a few ways to do what you want. One way, that I learned here on the forums, that seems simplier than what I used to do, is to add a command to the /etc/network/interfaces file that will execute your iptables script. Here is my file:```
# Smythies 2011.11.15 Can I execute my firewall script from here
#          instead of /etc/rc2.d? Add it.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
[COLOR=red]pre-up /home/doug/init/doug_firewall[/COLOR]
# The primary interface (d-link PCI card)
auto eth1
iface eth1 inet dhcp
# Local network interface (uses built in ethernet port)
auto eth0
iface eth0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255
```

---

### Post by marlow59 on 2012-08-27
Thanks a lot, I just tried it and restarted my computer. It works just fine.

---

