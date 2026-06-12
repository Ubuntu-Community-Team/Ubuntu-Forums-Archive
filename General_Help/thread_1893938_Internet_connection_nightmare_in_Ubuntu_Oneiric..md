---
title: "Internet connection nightmare in Ubuntu Oneiric."
date: 2011-12-11
forum: General Help
---

### Post by Styleion on 2011-12-11
Hi everyone,

I recently installed Ubuntu Oneiric Ocelot in my new desktop computer (AMD64 PC).
At first I think the Internet connection was just fine but for the last two days I've been unable to connect normally ...

The connects works for moments, but really slow and, after a while, it stops working at all, recovering after some minutes, and all over again...

When the connection isnt working i cant ping the nameservers in /etc/resolv.conf obviously. I tried putting aside Gnome Network Manager and tweaking /etc/network/interfaces for automatically configure my eth0 interface with DHCP, with no luck...

I cant believe this is happening in Ubuntu 11.10, in my other partition with Windows 7 the Internet is working properly.

What can I do?

---

### Post by Styleion on 2011-12-11
Bump!!!

---

### Post by Styleion on 2011-12-11
I uninstalled the Network-Manager and changed /etc/network/interfaces to:

auto eth0
auto eth0 inet dhcp

... and I'm not getting connection all, the interface eth0 doesnt go up, it cant get an IP from the DHCP..

---

