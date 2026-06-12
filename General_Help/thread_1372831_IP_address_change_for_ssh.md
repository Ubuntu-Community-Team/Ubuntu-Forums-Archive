---
title: "IP address change for ssh"
date: 2010-01-05
forum: General Help
---

### Post by A Feyn Man on 2010-01-05
I'm using crunchbang (jaunty) on an old desktop at home that I intend to use as an ssh server. I have everything set up and ready to go, I can ssh just fine if I'm on the same network (on my laptop) as the server, but when I tried remote access, I realized that I had the general IP (192.168.1.100) and that I needed to change the IP address to ssh remotely.

I have tried to manually change the /etc/network/interfaces file but have only gotten confused.

The question is what do I change and where in order to get a unique IP address for my ssh server to ensure a successful remote connection?

---

### Post by prshah on 2010-01-05
> **A Feyn Man said:**
> The question is what do I change and where in order to get a unique IP address for my ssh server to ensure a successful remote connection?

The 192.... family of IP addresses is for "internal" (ie, private LAN) use only. Your ISP's modem/router will have a proper "external" IP address. You will have to setup the modem/router to "forward" requests from remote machines to your internal SSH server 192.168.1.100. You can find more exact steps for this by checking the method required for your brand/make/model of router from [www.portforward.com](www.portforward.com)

You can get your "external" IP address by visiting a website such as [www.whatismyip.com](www.whatismyip.com)

You can also setup DynDNS (most DSL routers support this) to map your external IP to a host name (such as xxxxx.dyndns.org). This is necessary because most routers change the "external" IP on a regular/restart basis.

Post back if you have any questions or want more details.

---

### Post by Vaphell on 2010-01-05
internal 192.168.x.x are not visible from the other side of router. Imagine that LAN is the building that has the address written on the wall (public ip supplied by your ISP), but you don't know anything about the interiors, how many flats are there, etc. (lan adresses). All traffic has to be checked by the gatekeeper but you can build a door directly to a given apartment for special guests introducing themselves as SSH traffic - this is port forwarding (external_ip: port1 = internal_ip: port2).

you can add as many exceptions as you wish: for torrents (better download speeds), for multiplayer games (often required to host games), you name it.

---

