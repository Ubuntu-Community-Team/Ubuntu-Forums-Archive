---
title: "Need Help With Online Issues"
date: 2006-02-11
forum: General Help
---

### Post by maureliuswolf on 2006-02-11
I'm having an issue with enabling my wireless adapter. I click on enable in the network settings and it enables the adapter and then disables it automatically. Can anyone help me?

---

### Post by FlakJacket on 2006-02-11
I had this trouble too.  I think i solved it by turning on dhcp on my ethernet card but i'm not sure.

Flak

---

### Post by maureliuswolf on 2006-02-11
Thanks for your help, but can you help me with doing that? I don't know how.

---

### Post by FlakJacket on 2006-02-12
Run command > ```
kdesu kcontrol
``` > enter your user password > go to "internet and network" > network settings > click eth1 > click configure interface > bubble automatic dhcp.  This is assuming that you already have your wireless cards info in. Then, hopefully,  you should be able to enable the eth0.

Hope it helps,
Flak

---

