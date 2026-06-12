---
title: "Package/module network-drivers, livesystem"
date: 2010-10-04
forum: General Help
---

### Post by Butcher0 on 2010-10-04
I am building a custom Live-USB-system out of my Ubuntu. I have removed following:
* network-manager
* network-manager-gnome
* network-manager-pptp
and network-manager-pptp-gnome

When i run "ifconfig" after this, the only adapter that is visible is the loopback for localhost, no Wi-Fi and no LAN. 

I make a backup of the system with "remastersys".
The weird thing happens when I make a Live-USB out of the system. When i boot up with my USB with the live-system, the network drivers are back..
I run ifconfig, and it is suddenly aware of my Wi-Fi and LAN adapters again.

So what I hope to achieve, is to be able to boot up my custom-system from USB with no adapters recognized, I want the drivers to be gone, and I don`t want Ubuntu to try to discover any network adapter either.

Anyone who has experience and knows something that might come useful? ;)

---

