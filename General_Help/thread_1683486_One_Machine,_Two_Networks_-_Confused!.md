---
title: "One Machine, Two Networks - Confused!"
date: 2011-02-07
forum: General Help
---

### Post by justindublin on 2011-02-07
Hey,

I'm running a couple of cloud servers and having problems getting them to remain stable on the internal network of the host.

The settings I have from the provider are:
[IMG]http://dl.dropbox.com/u/3372660/IPlist.JPG[/IMG]

Based on that, does this looks configured right?


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
       hwaddress ether 00:00:d1:d0:3f:4d
       address 209.208.11.77
       netmask 255.255.255.0
       gateway 209.208.11.1

auto eth1
iface eth1 inet static
       hwaddress ether 00:00:d1:d0:3f:4d
       address 10.3.97.5
       netmask 255.255.255.0
       gateway 209.208.11.1
```

Thanks in advanced!

---

