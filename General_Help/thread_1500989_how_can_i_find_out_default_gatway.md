---
title: "how can i find out default gatway?"
date: 2010-06-03
forum: General Help
---

### Post by linkshift on 2010-06-03
my host has setup a vps for me but i dont know what is the default gateway
sorry, im a noob to linux networking... 

i actually need to find this out, so i can use it for vpn config. thanks!

---

### Post by efflandt on 2010-06-03
To find your default gateway for normal networking do **route -n** in a terminal, and the gateway at the bottom with 0.0.0.0 for destination and genmask and UG flags is the default gateway for your current networking.

If you do not get an IP automatically (dhcp) or that has not been configured, you would have to find out from someone who knows about that network.

---

