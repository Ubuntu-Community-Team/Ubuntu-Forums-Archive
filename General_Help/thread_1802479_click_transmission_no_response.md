---
title: "click transmission no response"
date: 2011-07-12
forum: General Help
---

### Post by alwayslost123 on 2011-07-12
Yesterday, I paused all processes and quited transmission as usual.  Today, I want to start it again but I cannot see the transmission GUI (  Applications > Internet > Transmission BitTorrent Client ).  I searched from Google and tried transmission-gtk -m.  The output is Segmentation fault :(

When I tried transmission-gtk %U
The output is as below
transmission-gtk: malloc.c:4636: _int_malloc: Assertion `victim->bk_nextsize->fd_nextsize == victim' failed.
Aborted


Anyone can help me to solve this issue, please ?

Thank you in advance ...

[Solved]
After I had posted here, I found a transmission update from Synaptic.  Then, I updated and the issue was resolved.  Quite strange, I tried to update many times before, but nothing.  Anyway, I would like to say thank to all.

---

