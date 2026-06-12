---
title: "Networking Trouble"
date: 2009-12-20
forum: General Help
---

### Post by Skidbladniir on 2009-12-20
Server System - No GUI.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 70.114.165.30
gateway 70.114.160.1
netmask 255.255.255.0
network 70.114.160.0
```sudo /etc/init.d/networking restart

* Reconfiguring network interfaces
SIOCADDRT: NO such process
Failed to bring up eth0

Sorry, probably typos. I typed that without seeing the screen. I was looking at my server's screen (One screen - VGA splitter). Please help.

---

### Post by Skidbladniir on 2009-12-20
Nevermind.  =X  I forgot my netmask ends with .224.

---

