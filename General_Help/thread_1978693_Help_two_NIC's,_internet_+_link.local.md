---
title: "Help: two NIC's, internet + link.local"
date: 2012-05-12
forum: General Help
---

### Post by vcrpcant on 2012-05-12
I have two network interfaces on my Ubuntu 10.04 desktop, one onboard and the other PCI.

I want to use one to acess the internet.
I want to use the other to connect directly, using a crossover ethernet cable, to another Ubuntu 10.04 desktop.

I have managed to do both things isolated, but not together.

After googling and experimenting I now need some help :confused:

Here's my fstab:

auto lo
iface lo inet loopback

#internet
auto eth5
iface eth5 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

#other machine
auto eth7
up route add -net 192.168.1.4 netmask 255.255.255.0 eth7

---

### Post by pbrane on 2012-05-12
you can only have one gateway. remove the gateway entry for the local eth interface and leave the one for the internet interface.

---

### Post by vcrpcant on 2012-07-01
Thanks :)

---

