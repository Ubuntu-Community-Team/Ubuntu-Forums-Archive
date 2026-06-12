---
title: "weird networking issue"
date: 2006-03-29
forum: General Help
---

### Post by calcium79 on 2006-03-29
Chances are I'm forgetting something ridiculously simple, but anyway...
I'm quite new to Linux, and I've decided to set up an old Pentium II in Ubuntu, and I stuck a wireless card in there (Netgear WG311T), which connects to a wireless router (Netgear WGT624) I had previously set this up with a different comp dual-booted with XP and it worked fine.
However, this time it reacts in a weird way. It's set up with WEP, I put in the ESSID, the WEP encryption and the fact that its hexadecimal. I've provided a host name, domain name and the address of the DNS server as the IP of the router (192.168.0.1) The wireless card seems to connect to the router, but doesn't get any further - it cannot ping other computers on the network or reach the internet.
Using iwconfig (or ifconfig, I forget) it shows a gigantic amount of errors sending from the card. At the routers end, it shows the computer as connected but doesn't show the name of the computer (which I figured would be the host name, in XP it's just the Computer Name)
Is there anything I'm missing?

---

### Post by jamesr on 2006-03-29
I do not normally help with wireless network Problems as I have limited experience of them when using linux.

But can you ping the router?
post the /etc/network/interfaces file ie```
cat /etc/network/interfaces
``` Also the DNS server is not normally the router.

---

### Post by calcium79 on 2006-03-29
Ahh, I see.
Yes I can ping the router, that works fine.
I'll try sticking in my ISP's DNS server.
And I will get back to you on the interfaces file if I need more help. :)

---

