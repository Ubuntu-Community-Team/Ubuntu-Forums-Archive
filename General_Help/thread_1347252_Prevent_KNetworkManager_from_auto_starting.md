---
title: "Prevent KNetworkManager from auto starting?"
date: 2009-12-06
forum: General Help
---

### Post by Roasted on 2009-12-06
On my spare computer here I'm running Kubuntu with 2 NIC's, one for DHCP use so I can get external access, and one for static use which I will use to image computers via FOG with PXE boot.

As a common practice with FOG when I used Ubuntu heavily, I would disable Network Manager from startup and I'd edit the network interface file accordingly to the two NICs.

Since I've been venturing in KDE land, I'm trying to mimic the same sort of setup. How can I prevent KNetworkManager from auto starting so ONLY the network interface file is what gets looked at for assigning addresses to the interfaces?

---

### Post by collinp on 2009-12-06
I did a Google search, and the best that I could come up with was a section of the older NetworkManager wiki page:

[https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

It's for older versions of Ubuntu, but it may still be helpful.

---

### Post by kxmas on 2009-12-06
> **Roasted said:**
> On my spare computer here I'm running Kubuntu with 2 NIC's, one for DHCP use so I can get external access, and one for static use which I will use to image computers via FOG with PXE boot.

As a common practice with FOG when I used Ubuntu heavily, I would disable Network Manager from startup and I'd edit the network interface file accordingly to the two NICs.

Since I've been venturing in KDE land, I'm trying to mimic the same sort of setup. How can I prevent KNetworkManager from auto starting so ONLY the network interface file is what gets looked at for assigning addresses to the interfaces?

in previous versions of ubuntu, any interface configured by hand in /etc/networking would not be managed by network-manager.  I assume this is still true.

---

### Post by Roasted on 2009-12-06
I assume this is still true with KDE land?

EDIT - it appears that it's still true. I edited it the same way as I did in Gnome and rebooted and it was fine, one DHCP interface, one static interface. I just remember in Gnome having to remove network manager or it could be a beeyotch, but knetworkmanager doesn't seem to effect anything.

Anyway, what if I want to add/remove startup apps anyway? How do I do that in KDE?

---

