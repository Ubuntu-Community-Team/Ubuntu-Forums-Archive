---
title: "Network Slowdown after last 10.04 update."
date: 2010-07-03
forum: General Help
---

### Post by McRat on 2010-07-03
Anyone seeing a dramatic slowdown and "PAGE NOT FOUNDS" after the latest updates?

It even happens on LAN activity.  Peak speed is excellent, the ability to resolve both local and WAN addresses is very spotty.

Machine is a newer Clone with AMD Phenom II dual core with 2gb running 10.04 32-bit with Gnome.  Network is Gigabyte MoBo 1000-T ethernet hardwired to Dlink router into cablemodem.

XP and Win7 aren't affected.

It was ripping this morning, but right now, is pretty much crippled.

---

### Post by McRat on 2010-07-03
It's a Realtek ethernet chip.

---

### Post by waloshin on 2010-07-03
No what browser are you running? Try Chrome.

---

### Post by McRat on 2010-07-03
> **waloshin said:**
> No what browser are you running? Try Chrome.

Chrome and Firefox exhibit the same, but it's the LAN function that I need more than browsing.  I found another thread about it.  Guess I need to learn "rollback".  Trying to figure that out.

Something else really weird happened, I don't know if it's related.  It showed 10 cloned MAC addresses on the network, so I thought it was router related.

---

### Post by McRat on 2010-07-04
Not sure why this fixed the LAN part of it, but I removed the direct DNS name from the IPv4 settings and let it go automatic, then it worked for Internet.  But Win machines set up with the same direct DNS name still fly.

Not sure why this became an issue after the update, but I did not rollback, and today it works.

---

