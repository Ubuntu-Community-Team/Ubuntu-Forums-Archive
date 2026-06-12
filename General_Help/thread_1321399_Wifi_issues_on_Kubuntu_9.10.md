---
title: "Wifi issues on Kubuntu 9.10"
date: 2009-11-10
forum: General Help
---

### Post by bruno.braga on 2009-11-10
Just to leave documented. As soon as I installed the Kubuntu 9.10, to try out the KDE, I noticed the following issues regarding the Wireless Network:

[LIST]
[*]In case your first attempt fails (password or security type wrong), you can not connect anymore
[/LIST]

[INDENT]I solved this by deleting the stored connection (at Manage Connections > Wireless) and trying it again[/INDENT]

[LIST]
[*]Trying to connect does not work anyway
[/LIST]

[INDENT]I solved this by restarting the network manager: (from Terminal)
```

killall knetworkmanager
knetworkmanager
```
[/INDENT]

Just to leave documented, in case anyone faces the same issues.

This really irritated me, as Gnome was just working fine. Reading more about this, it seems KDE does not handle Wifi as well as Gnome. 

**Machine**: Toshiba Dynabook TX/66C
**Device**: Atheros, AR5001 Wireless Network Adapter

---

