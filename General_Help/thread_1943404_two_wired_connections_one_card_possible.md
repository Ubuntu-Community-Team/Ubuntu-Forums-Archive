---
title: "two wired connections one card possible?"
date: 2012-03-19
forum: General Help
---

### Post by davidvandoren on 2012-03-19
Hi there.

I want to connect two Ubuntu pc on a local network so they can share files using samba.  
I want each pc connecting to the INTERNET via ppoe wired on its own at the same time.

How can I connect to the INTERNET without disconnecting from the wired connection? 

Or do I need two network cards? It's no problem with windows.

---

### Post by 2F4U on 2012-03-19
You could use a router, connect both machines to the router and connect the router to the internet.

---

### Post by davidvandoren on 2012-03-19
Thanks 

I am using a network switch that connects to the INTERNET.
However, I want to connect to the other computer and the internet at the same time. But when I try to connect to the INTERNET the wired connection gets disconnected. 

Am I doing something wrong or is it not possible at all. 

By the way I am using a second usb Ethernet card but that's only a temporary solution.

---

### Post by efflandt on 2012-03-19
PPPoE is effectively isolated from the ethernet wire that carries it in that PPPoE has no ethernet IP (only a network IP inside its tunnel), so any regular ethernet network on the wire would totally ignore it.

It is quite possible to assign an IP address to eth0 and have pppoe0 on that same wire.  Some people do that for a combination modem/router, so even if they switch it to bridge mode, they can still access the modem config by its IP address.  I did something similar years ago, but with a dummy IP for ethernet that was a dead end with no routing just to make sure nothing came in on the same line handling PPPoE.

But I do not know if the switch would know which way to direct the PPPoE signal, or if that would even be able to find your modem.

If your modem does not have a router built-in, can't you afford a low cost broadband router that could handle the PPPoE and protect your LAN from the internet?  One I got some time ago was about $5 after discounts and rebate and another one was about $15.

---

