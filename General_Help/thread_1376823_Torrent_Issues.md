---
title: "Torrent Issues"
date: 2010-01-09
forum: General Help
---

### Post by DareArkin on 2010-01-09
Okay, so on my Ubuntu I tried Transmission, Ktorrent, and Bittornado. None can find peers.

Yet on my Win7 Box, everything can find peers. 

Both computers are hooked to the same router and the same modem. What the hell's going on?

---

### Post by happyhamster on 2010-01-09
Does the router have a firewall? If so, you'll probably have to forward a few ports to be able to get things running. For example: ktorrent uses 1 for data, 1 for UDP trackers and 1 for DHT. All 3 ports have to be forwarded in the router's firewall.

---

