---
title: "Retain network settings for each card"
date: 2006-03-02
forum: General Help
---

### Post by OMRebel on 2006-03-02
I have Breezy installed on an older laptop.  I have to put in a PCMCIA ethernet card up here at the office to use my laptop.  However, I have to enter in a static IP for it at that time, as we don't run DHCP.  When I take my laptop home, I remove the card and put in a wireless card.  However, I have to change my network settings (change everything back to DHCP and remove the DNS entries) to get on my network at my house.  

Is there a way I can configure this so that I don't have to keep changing these settings and it'll recognize that when I'm using my enternet card to use a static ip and dns entries, but when I'm using my wireless card it'll revert to using DHCP?

Thanks.

---

### Post by o_fortuna on 2006-03-02
[QUOTE=OMRebel]I have Breezy installed on an older laptop.  I have to put in a PCMCIA ethernet card up here at the office to use my laptop.  However, I have to enter in a static IP for it at that time, as we don't run DHCP.  When I take my laptop home, I remove the card and put in a wireless card.  However, I have to change my network settings (change everything back to DHCP and remove the DNS entries) to get on my network at my house.  

Is there a way I can configure this so that I don't have to keep changing these settings and it'll recognize that when I'm using my enternet card to use a static ip and dns entries, but when I'm using my wireless card it'll revert to using DHCP?

Thanks.[/QUOTE]
Get network-manager from Synaptic. I'm not sure how good it is, but supposedly it keeps track of such things for different places. The other option is to use "locations" in the Networking under System-->Administration, but I've had funny experiences with those, so I'd stick with network-manager.

---

### Post by darth_vector on 2006-03-02
the best way to configure your networking is thought the /etc/network/interfaces file. there always seem to be problems with the gnome networking control pannels and things.

---

