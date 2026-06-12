---
title: "looking for pristine /etc/network/interfaces"
date: 2006-06-15
forum: General Help
---

### Post by Fritti on 2006-06-15
Hiya,

I managed to screw up my /etc/network/interfaces while mucking about and trying to make a default qemu bridge setup.

Now I can't find a way to restore it to a pristine state however; forcible reinstalling the 'ifupdown' package doesn't work...

Can anyone post their default Dapper version of the file? Thanks!

---

### Post by caserio on 2006-06-15
Hi,
cat /etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by mlind on 2006-06-15
Here's mine

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

---

### Post by Fritti on 2006-06-15
Thanks a bunch, that's exactly what I was looking for. One last thing, do you have all those interfaces in your system? (ie is the list dynamically generated somehow?)

---

### Post by mlind on 2006-06-15
[QUOTE=Fritti]Thanks a bunch, that's exactly what I was looking for. One last thing, do you have all those interfaces in your system? (ie is the list dynamically generated somehow?)[/QUOTE]

It's generated dynamically, but I no idea about chain-of-responsibility here..
See if [http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html) helps.

---

