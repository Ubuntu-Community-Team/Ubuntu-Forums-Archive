---
title: "problems with access within LAN"
date: 2006-02-14
forum: General Help
---

### Post by comrade_chimp on 2006-02-14
I have 2 machines running ubuntu 5.10, a desktop and a laptop. Both are connected to a wifi router and via that to the internet. The wifi router registers with a dynamic dns service and various ports are forwarded to the desktop machine so that I can serve web pages, use ssh, etc. This all works perfectly.

However, using either one of the 2 machines I cannot access the other within the LAN either by IP address or machine name. I can't ssh, ping, nothing. From either machine I can ping the router (192.168.0.1) and from either I can ssh to the desktop via the dynamic dns url (the router forwards port 22 to the desktop). Attempting to ping either machine's LAN IP from the other machine gets me "Destination Host Unreachable". Both machines can successfully ping themselves on the IP the router assigns them (192.168.0.2 for the desktop, 192.168.0.3 for the laptop).

It looks to me like something pretty fundamental is missing but I'm a bit of a linux noob so I'm not sure what.

---

