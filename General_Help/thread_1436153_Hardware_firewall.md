---
title: "Hardware firewall"
date: 2010-03-22
forum: General Help
---

### Post by morvol on 2010-03-22
Hello. I would like to create a hardware firewall. I just dont know how i can do it. I know that i need at least 2 NIC cards but i dont know about the configuration of this.

Is there any guide or somethink that can show me how to create a propert one? I need any informations that you might have couse this is my final "article" for my univercity :D

Thanks for your time

---

### Post by gmargo on 2010-03-22
To do a firewall in Linux you'll need to understand "iptables" and the packet flow.  Google on iptables, there's plenty of tutorial info; here's Wikipedia: [http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables) which has a nice diagram.

To create firewall rules you can either write iptables commands yourself (hardest, but you'll learn a lot) or graduate up to one of the firewall packages, like "ufw" or "shorewall".

---

### Post by morvol on 2010-03-22
so i only need to configure my iptables? I dont need to install any package for a firewall?

---

### Post by Enigmapond on 2010-03-22
> **gmargo said:**
> To do a firewall in Linux you'll need to understand "iptables" and the packet flow.  Google on iptables, there's plenty of tutorial info; here's Wikipedia: [http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables) which has a nice diagram.

To create firewall rules you can either write iptables commands yourself (hardest, but you'll learn a lot) or graduate up to one of the firewall packages, like "ufw" or "shorewall".

Think you missed it. They are talking about building a "Hardware" firewall and iptables is a "Software" firewall. Sorry morvol, I don't know what's involved in building one...;)

EDIT: apologies all around...I guess that IS what he wanted..Yes Ubuntu comes with it's own firwall and all that is necessary to do is configure the iptables...correct..:)

---

### Post by pbrane on 2010-03-22
Two NIC cards, on facing the WAN and one facing the LAN? Sounds like you want to create a "border" box. A proxy using iptables. You may need to look up linux routing too. Since you said "create" I assume you don't want to buy a firewall appliance. Like the other posters pointed out you need to google for *iptables*, *setting up two NICs on linux*, etc.

---

### Post by morvol on 2010-03-22
well let me explain correctly. I need a "dedicated hardware firewall" , lets say that i need to have a firewall for a datacenter.
The only clues that i had is that i need to make it a gateway and have 2x NIC cards.. one for external and one for internal. 

Btw thanks for your quick reply's :D

---

