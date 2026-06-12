---
title: "Printer Sharing Via Avahi"
date: 2010-04-08
forum: General Help
---

### Post by Zerocool3001 on 2010-04-08
I've been trying to set up Ubuntu to share a network printer so it can be discovered by other computers (largely Macs) on the network. The printer itself is on the network, being hosted by an external print server. I am able to add the printer in CUPS using the hplic protocol and I have CUPS set to share printers (althought not over the internet). However, I can't find good documentation on announcing this printer with Avahi. I don't know what printer type I should be using (ipp,lpd,etc.) or what to put in and call the service file.

I realize the printer is already available to the network (I cant tell if it's lpd, jetdirct, or something else) but I would like it available via Bonjour for the other computers in the house. I also think at least one of the things I want to print from requires printers be available this way (i.e. shared from a Mac) because it doesn't have printer drivers of it's own.

Any help anyone could give would be much appreciated.


P.S. The printer is an HP LaserJet 6.

---

