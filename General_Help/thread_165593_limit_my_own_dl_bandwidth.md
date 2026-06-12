---
title: "limit my own dl bandwidth ?"
date: 2006-04-24
forum: General Help
---

### Post by bsmith1051 on 2006-04-24
I'm trying to setup a workstation to run klibido (to download alt-binary newsgroups) but I don't want it to max the line.  I'm accustomed to apps like Azureus which have their own bandwidth throttling.  How can I make klibido do the same?

All the how-to's I've been able to find seem to apply to servers or routers rather than to one's own workstation.

---

### Post by bsmith1051 on 2006-04-25
I was able to solve this with wondershaper!
> sudo wondershaper eth0 2400 240

---

### Post by cypresstwist on 2006-04-27
Or you could also try trickle
trickle -d 20 -u 10 azureus

---

