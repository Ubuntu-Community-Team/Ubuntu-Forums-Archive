---
title: "GUI vs /etc/network/interfaces"
date: 2011-06-01
forum: General Help
---

### Post by krisdotca on 2011-06-01
I just modified my network configuration by going through the  System-->Preferences-->Network Connections screen. I'm curious as to why these settings don't also show up in  /etc/network/interfaces?

Regards, Kris

---

### Post by seawolf167 on 2011-06-01
What kind of changes did you make? As far as I know, only setting something like a static IP for your box would show up in /etc/network/interfaces, DNS servers would be in /etc/resolv.conf

That said, maybe the network-manager (or network-manager-gnome) has stored the configurations elsewhere? Hopefully someone more knowledgeable in this area can help.

---

