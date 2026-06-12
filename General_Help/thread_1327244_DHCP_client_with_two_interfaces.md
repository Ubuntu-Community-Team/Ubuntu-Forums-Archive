---
title: "DHCP client with two interfaces"
date: 2009-11-15
forum: General Help
---

### Post by sbw87 on 2009-11-15
Hi, 
I've got a client PC with two network interfaces (LAN und WLAN) that are to be connected to my dhpcd ubuntu server. Unfortunately, this doesn't work: Only the LAN interface gets an IP address while the WLAN card gets none. It doesn't matter whether I use dynamic or static addresses.

What can I do?

Thanks
S.

---

### Post by Iowan on 2009-11-15
The interfaces connect to the same DHCP server but should get different IP subnets? You *might* be able to set up your DHCP server to do that, but the client machine may still request only until it gets an address (one).
Connection-wise,  what differentiates between the LAN connection and the WAN connection?

---

