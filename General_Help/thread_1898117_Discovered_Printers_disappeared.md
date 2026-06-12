---
title: "Discovered Printers disappeared"
date: 2011-12-20
forum: General Help
---

### Post by shaneo1 on 2011-12-20
Today one of my Ubuntu 11.10 Desktop machines has lost sight of the discovered printers shared from my print server using CUPS. None of the settings for seeing shared printers has been changed and the CUPS server on the host is working fine.  A laptop I have with Ubuntu 11.10 sees all the printers and so does the windows counterpart desktops.  Just this one computer.

Does anyone know why this would have happened.  I have cycled reboot a couple of times with no affect and restarted the cups service via sudo, but still nothing.

When I go to add a printer I can see the printers shared from the host but can not add them.  I have a local USB printer which works fine, but that too is not shared on the network back to the host CUPS server.  

I'm stumped.  Please help thanks in advance.

---

### Post by shaneo1 on 2011-12-23
Hehe, Fixed it, forgot I installed a firewall, and then stopped it, restarted the machine and forgot about it.  All working now.  

Thanks for the support guys  :KS

---

