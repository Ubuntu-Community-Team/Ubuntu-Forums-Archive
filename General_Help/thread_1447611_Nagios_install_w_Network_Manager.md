---
title: "Nagios install w/ Network Manager"
date: 2010-04-05
forum: General Help
---

### Post by deznuts05 on 2010-04-05
Hello,

I started my install of Nagios on Ubuntu 9.10 w.Network Manager. I later found out that network manager doesn or should I say it makes configuring static ip's difficult and that the most direct approach would be to edit the interfaces file.

Part of this I read that network manager could be removed, which I did however now with network manager deleted from the system and the interfaces file configured for static. I am able to view the internet however I've seem to have loss the ablity to see my Nagios page locally.

Any help would be great.

Thank you

---

### Post by zvacet on 2010-04-05
You can install **wicd** from synaptic and set your static with it.

---

### Post by deznuts05 on 2010-04-06
Thanks! I just ended up rebuilding the machine. Once the OS install was complete I left Network Manager installed and just use sudo nano the interfaces file

---

