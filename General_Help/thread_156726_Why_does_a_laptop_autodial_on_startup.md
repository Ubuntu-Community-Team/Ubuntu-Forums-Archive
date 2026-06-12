---
title: "Why does a laptop autodial on startup?"
date: 2006-04-07
forum: General Help
---

### Post by DavidTangye on 2006-04-07
For some reason a friend's laptop dials up their ISP on laptop bootup. I removed /etc/rc2.d/S14ppp but it still dials up. OK, so maybe S14ppp is not even a dialup script, so what is it? If it starts a support daemon why does dailup work when it is removed?

'ps' reports the command running as '/usr/sbin/pppd call ppp0'

To confuse me more it just started happening a few days ago, but I cant recall changing any config.

Anyway, the main question is - why does the laptop autodial on startup?

---

