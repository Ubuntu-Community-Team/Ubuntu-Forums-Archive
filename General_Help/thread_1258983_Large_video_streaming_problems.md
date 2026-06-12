---
title: "Large video streaming problems"
date: 2009-09-05
forum: General Help
---

### Post by jon64 on 2009-09-05
Hi, I have a file media server set up with ubuntu desktop. While streaming small(under 5GB) movies everything works great but when I try to watch HiDef movies(8GB+) I start to getting stoppage between every second. I'm not sure if it's a buffering issue but I don't think I can change the Windows Media Player Classic buffer size or there could be a problem with my network configuration. I'm going to be listing my interface configuration down below. If you need more information, don't hesitate to ask. Thanks :D

**/etc/network/interfaces**
```
auto lo
iface lo inet loopback

#static ip address:
auto eth0
iface eth0 inet static
address 192.168.0.104
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0
gateway 192.168.0.1
#dns-nameservers 192.168.0.104
#dns-search ns1.corruptednedias.com
#dns-domain corruptedmedias.com

auto eth1
iface eth1 inet dhcp
```

---

### Post by jon64 on 2009-09-08
bump :popcorn:

---

