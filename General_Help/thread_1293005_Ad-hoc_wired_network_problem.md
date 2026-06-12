---
title: "Ad-hoc wired network problem"
date: 2009-10-16
forum: General Help
---

### Post by pratik_narain on 2009-10-16
I have a PC with linux mint 7 gloria installed on it and a laptop with ubuntu 9.04. I've got a crossover LAN cable to connect both for file as well as internet connection sharing. But when I connect the cable on both, i don't get connected. Please help me.

---

### Post by Giblet5 on 2009-10-16
Unless you're running a DHCP server on one of those boxes, you'll have to configure a static IP address on each box and make /etc/hosts entries for those IP addies.

I take it you have a Cable/DSL router/firewall that also provides DHCP? Well, a crossover cable takes that out of the mix.

You'd be much happier adding a network hub for $10.

You can try to get Network-Manager to let you set up a static IP profile, but I've never done that.

I remove Network-Manager as step #2 of an install. I use WiCD instead and it just works.

Worst-case, you can remove network-manager and configure your network manually.

/etc/network/interfaces is where the config is set on systems w/o network-manager (most other unix-like OSes). An entry like this will work for one system ```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
```

and like this for the other ```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
```

On each system, execute ```
sudo /etc/init.d/networking restart
``` and the new net config will be in effect.

---

### Post by pratik_narain on 2009-10-18
I have modified the files as you told. Now connection is being established but I still cannot share internet connection or any files even after restarting the netwok interface.

---

