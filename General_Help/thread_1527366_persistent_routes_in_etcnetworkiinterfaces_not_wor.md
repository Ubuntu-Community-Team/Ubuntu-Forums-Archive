---
title: "persistent routes in /etc/networki/interfaces not working anymore with 10.04 LTS"
date: 2010-07-09
forum: General Help
---

### Post by deracled on 2010-07-09
I've been using "[FONT=Courier New]up ip route....[/FONT]"  in /etc/network/interfaces  to configure persistent routes on several servers. This was working fine up to at least 8.04LTS but now with 10.04LTS it just stopped working. The route just doesn't get applied even though it works fine when I type it in manually.

Here's my interfaces file, using example IP's:

[FONT=Courier New]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 10.10.1.25
  netmask 255.255.255.0
  network 10.10.1.0
  broadcast 10.10.1.255
  gateway 10.10.1.1
  up echo Interface $IFACE going up | /usr/bin/logger -t ifup
  up ip route add 10.10/16 via 10.10.1.1 mtu 1280 dev $IFACE [/FONT]


I find adding persistent routes directly into the interfaces file much easier than creating /etc/network/if.up.d/ scripts and worked well up to now.

Thanks for helping out 
Doro

---

