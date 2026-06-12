---
title: "Recent cups update broke Brother printer"
date: 2010-03-23
forum: General Help
---

### Post by hangfire on 2010-03-23
The recent 9.10 CUPS update reverted my Brother MFC-640cw device driver URI from **socket://ip : port** to an undesired notation for USB. This broke printing until I changed it back AND did a **sudo /etc/init.d/cups** restart.

This, by the way, brings up an issue I have with the install of this driver. You have to intuit the socket notation, for even if you discover the printer using the wizard on the network, it still installs it with a USB URI. Weird. Not sure whose fault that is, Brother or CUPS.

The driver is actually for the MFC-210C, as provided by the Brother web site.

-HF

---

