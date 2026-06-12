---
title: "wired network disconnected - but it isn't"
date: 2012-09-24
forum: General Help
---

### Post by elj4176 on 2012-09-24
(using 12.04 32 bit) Lately I have been getting a notification that says 'wired network disconnected' - but it isn't disconnected. I can still ping network resources and browse the web. It doesn't appear to be causing any problems but it is getting annoying.

I have tried a new ethernet cable, different port on the switch, different switch, new ethernet cable at the switch. The only thing I can think of that I have not tried is a new NIC. 

It seems to be something with one of the latest updates. Anyone else seeing this problem?

---

### Post by albandy on 2012-09-24
If your connection is dhcp and is always connected to the same network cable, you can do the following (but this trick may slow you boot if your network cable is not connected)

Add these lines to /etc/network/interfaces:

auto eth0
iface eth0 inet dhcp

---

### Post by elj4176 on 2012-09-24
Thanks but I don't think there is actually anything wrong with my connection. I think 12.04 has a problem of some sort. I'm basically posting to see if anyone else is seeing the same thing.

---

