---
title: "HP Printer loses connection"
date: 2012-01-06
forum: General Help
---

### Post by Jan Greeff on 2012-01-06
My HP Officejet 6313 ethernet network connection via the router loses its connection from time to time. 

This happens every time when the other computer on my network is switched on, in which case connection is re-established when the networked machine is switched off. It also happens when upgrades are downloaded and the last time it happened for no apparent reason. 

The system usually re-establishes the connection at some stage, but this time it is staying dead. 

This has happened to me on Ubuntu 10.04, 10.10 and now on 11.04. 

There seems to be a conflict between CUPS and HPLIP, and I do not know how these systems work together, if at all. 

This has been an ongoing source of frustration ever since I started using Ubuntu, is there a way out?

---

### Post by ajgreeny on 2012-01-06
Might this be related to the need for a static IP address for the printer, as I suspect that you have probably given it a connection with DHCP.  This happened before I gave our router connected HP machine a static IP.  It was actually still connected to the router, but if I remember correctly, a change of IP meant that other computers could not find it when trying to print.

---

### Post by Jan Greeff on 2012-01-06
Thanks ajgreeny. Are you able to explain to an illiterate how to go about giving the machine a static IP?

---

