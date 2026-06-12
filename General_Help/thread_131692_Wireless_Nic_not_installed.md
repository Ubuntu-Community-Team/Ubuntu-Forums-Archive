---
title: "Wireless Nic not installed"
date: 2006-02-16
forum: General Help
---

### Post by ril560 on 2006-02-16
I know there is probably something Im not doing, but it doesnt appear as though my wireless card is installed. I can get the driver to install using ndiswrapper, but the command ndiswrapper -l displays:

Installed ndis drivers:
netprism         driver present

I know from reading the guides and posts here that there should be a line that says hardware present too. I have a Dlink DWL-650 running on a PCMCIA Texas Instuments PCI1451 PC card Cardbus Controller. The card is being seen in Device manager as an "Unknown Device". I know the card works in windows. Any help would be apprieciated.

---

### Post by Bakerconspiracy on 2006-02-17
You still need to load the module and modulate, read the Load Module section of the [installation guide]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation").

---

### Post by ril560 on 2006-02-17
Thanks ill try that out

---

