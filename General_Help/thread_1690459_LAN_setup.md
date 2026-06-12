---
title: "LAN setup"
date: 2011-02-18
forum: General Help
---

### Post by vat with tux on 2011-02-18
[LEFT]Hello all.:)
I'm having ubuntu 10.04 on my pc.
How can i setup LAN between two systems in ubuntu?

[/LEFT]

---

### Post by cjhabs on 2011-02-18
> **vat with tux said:**
> [LEFT]Hello all.:)
I'm having ubuntu 10.04 on my pc.
How can i setup LAN between two systems in ubuntu?

[/LEFT]


If all you have is 2 systems, then you need to connect them together via an ethernet switch or hub, or even using a network cross-over cable.

Then you need to allocate each machine a static IP address that is on the same subnet as the other - 192.168.1.2 and 192.168.1.3 would be common choices with a 255.255.255.0 subnet.

---

### Post by gordintoronto on 2011-02-18
If you have two computers both connected to the same router, you have a LAN.

What do you actually want to do? Share files?

---

### Post by vat with tux on 2011-02-20
i want to share files. I want to connect two PCs using LAN cable.

---

### Post by cjhabs on 2011-02-20
> **vat with tux said:**
> i want to share files. I want to connect two PCs using LAN cable.

If you connect them directly then you need a network cross-over cable that crosses over the transmit and receive signals.

---

### Post by YesWeCan on 2011-02-20
i have a PCI ethernet card that does the cross-over automatically, but my mobo ethernet does not.

---

### Post by vat with tux on 2011-02-21
> **cjhabs said:**
> If you connect them directly then you need a network cross-over cable that crosses over the transmit and receive signals.
I'm able to connect 2 PCs using the same cable in windows. 
So i suppose it is cross-over cable.:) 
But i don't know the LAN setup procedure in ubuntu 10.04. 
So if anyone knowing then please tell me that procedure.

---

