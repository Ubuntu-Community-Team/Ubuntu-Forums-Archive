---
title: "apt-cacher: Very high CPU usage"
date: 2011-08-01
forum: General Help
---

### Post by imbjr on 2011-08-01
Lucid server 10.04.3

Came into the computer room this morning and wondered why the server box was humming hard. htop revealed that apt-cacher was consuming nearly 100% of the CPU. This has happened once before to my knowledge, when the server was @ version 10.04.2.

Googling reveals previous bugs with this outcome, but it looks like the situation should no longer be happening.

BTW I have a quite slow Internet connection, around 60kbytes/s.

Any suggestions?

---

### Post by imbjr on 2011-08-03
Well, it happened again this morning.

I've un-installed the proxy and installed apt-cacher-ng which seems to be the way to do things now.

---

