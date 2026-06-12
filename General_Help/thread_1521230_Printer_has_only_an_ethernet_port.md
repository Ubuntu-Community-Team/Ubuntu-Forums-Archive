---
title: "Printer has only an ethernet port"
date: 2010-06-30
forum: General Help
---

### Post by unckybob on 2010-06-30
Thanks for looking at this thread. 

HP Laserjet 8000N printer with only an ethernet port coming out of it. 

Everything I've looked at tells you how to share a printer that is already connected to a system (ie a computer) on your network. Since all this printer has is an ethernet port I assume I have to connect it to my router and print from one of the other computers connected to the router. 

Can someone please help?

---

### Post by davidmohammed on 2010-06-30
first, connect the printer directly to your PC and make sure you can print to it.

When you've done that then disconnect and connect to your router.  You'll need to either give it a static IP address or if your router gives it an IP address via DHCP, then configure your printer to accept DHCP requests.  All of this should be explained in your printer manual.

When done, in ubuntu, open a terminal and make sure you can see the printer.

ping <ip address>

If your printer is given an IP address, find what it is via your router menu page.

change your printer driver to find a network printer and give it your IP address.

---

### Post by sgosnell on 2010-06-30
Install hplip from the repositories.  Then connect the printer to your router, and have hplip find it.  You can actually just install a new printer from /System/Administration/Printers/New, and have it find the network printer, but hplip gives you more control and some additional functions.

---

### Post by unckybob on 2011-12-24
This printer has an odd kind of parallel port on it which can be used if you have the proper cable. I found out by taking it to a place that recycle ink cartridges and the guy there was able to tell me what kind of cable I needed. Then I just ordered one on eBay.

---

