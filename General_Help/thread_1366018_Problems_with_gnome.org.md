---
title: "Problems with gnome.org?"
date: 2009-12-27
forum: General Help
---

### Post by noloader on 2009-12-27
Hi All,

Is anyone else having problems getting to gnome.org (for example, [www.gnome.org]("http://www.gnome.org") and developer.gnome.org)? It pings fine, but I have not been able to connect over HTTP for some time. Is there a maintenance window open?

Jeff

$ traceroute -p 80 [www.gnome.org]("http://www.gnome.org")
traceroute to [www.gnome.org]("http://www.gnome.org") (209.132.180.167), 30 hops max, 60 byte packets
 1  firewall.home.pvt (192.168.1.1)  0.525 ms  0.663 ms  0.700 ms
 2  dsl.home.pvt (172.16.1.1)  4.617 ms  7.415 ms  10.008 ms
 3  * * *
[SNIP]
13  * * *
14  redhat-2.border2.phx004.pnap.net (69.25.121.30)  152.562 ms !X * *
jeffrey@Gauss:~$

---

### Post by abeisgreat on 2009-12-27
> **noloader said:**
> Hi All,

Is anyone else having problems getting to gnome.org (for example, [www.gnome.org]("http://www.gnome.org") and developer.gnome.org)? It pings fine, but I have not been able to connect over HTTP for some time. Is there a maintenance window open?

Jeff

$ traceroute -p 80 [www.gnome.org]("http://www.gnome.org")
traceroute to [www.gnome.org]("http://www.gnome.org") (209.132.180.167), 30 hops max, 60 byte packets
 1  firewall.home.pvt (192.168.1.1)  0.525 ms  0.663 ms  0.700 ms
 2  dsl.home.pvt (172.16.1.1)  4.617 ms  7.415 ms  10.008 ms
 3  * * *
[SNIP]
13  * * *
14  redhat-2.border2.phx004.pnap.net (69.25.121.30)  152.562 ms !X * *
jeffrey@Gauss:~$

I can't reach it either, they must be having server issues.

---

