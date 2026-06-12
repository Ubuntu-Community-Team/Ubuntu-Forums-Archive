---
title: "Is something wrong?"
date: 2009-07-05
forum: General Help
---

### Post by nexoncore on 2009-07-05
My internet connection has started being lowsey, claiming sites are offline when they are not and timing out a great dea ( Fire Fox ). I have also noticed that running firefox causes by dual cores to both run at 100%.

I then booted the live CD and everything was fine, but I havent installed anything on the ubuntu on my hdd, its the same as whats on the live cd.

Ontop of that, my laptop has recently been overheating on a few hourly basis. I am wondering if this is because of a dodgy recent update or a flaw in firefox.

---

### Post by moster on 2009-07-05
It may sound stupid but it wont hurt. Clear history of your firefox. Everything.

---

### Post by nexoncore on 2009-07-05
have, also used apt-get update to see if there had been a patch or something.

---

### Post by matrixblue on 2009-07-05
> **moster said:**
> It may sound stupid but it wont hurt. Clear history of your firefox. Everything.

Also disable your extensions and add-ons and see if it makes a difference.

---

### Post by HermanAB on 2009-07-05
Howdy,

In my experience it can be due to two things:
1. Adobe Flash plugin
2. Lame DNS

Disable the Flash plugin and test your DNS in /etc/resolv.conf using dig:
$ dig @nameserveripaddress [www.yahoo.com](www.yahoo.com)

Delete the slow one or put the fastest one at the top of the list.

---

