---
title: "laptop won't connect to the internet"
date: 2009-11-26
forum: General Help
---

### Post by matt12345 on 2009-11-26
well my sisters laptop won't connect to the internet. When we checked the drivers, it said that the driver that connects to the internet was not enabeled. So we enabeled it and nothing else changed. Oh and the current version of ubuntu is 8 ( I don't really knoiw what the full version is, but I would assume that its like 8.10)


so can anyone help out? :popcorn:

---

### Post by Iowan on 2009-11-26
Version will be either 8.04 (Hardy) or 8.10 (Intrepid). How did you check for drivers enabled? From a terminal, check for IP address:```
ifconfig -a
``` If eth0 (assuming wired connection) has valid IP address, check for valid DNS servers ```
cat /etc/resolv.conf
```

---

### Post by matt12345 on 2009-11-26
I checked the drivers by: system>admin>Hardware Drivers



Back to the matter, the laptop isn't connecting for the first time on this connection. It worked fine a few weeks ago, now it won't connect. When we checked the drivers, it said that the internet driver was not enabeled.

---

