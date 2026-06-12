---
title: "Connecting a printer"
date: 2010-03-20
forum: General Help
---

### Post by Rogermat on 2010-03-20
I am just starting on Ubuntu and all is ok except I cannot successfully connect my printer. This is a Brother
DCP-135 which has worked well until I switched to Ubuntu.
I have loaded the printer CD and a window for test message appears in Ubuntu. When I click on this button the panel on my printer briefly shows' Receiving Data' then reverts to the standby display '100% normal' and nothing is printed.

I have looked through the Ubuntu directory of printers and tried entering other Brother model numbers, but still no joy.

I've also looked in this directory to identify a printer model of any make that is recognised, but can't find any models listed there that are currently available on the market  for me to buy.

Can anyone help please?

---

### Post by Dayofswords on 2010-03-20
model of the printer would help greatly

---

### Post by anagor on 2010-03-20
I think that you should install the following packages, using either synaptic or command line, however you prefer:
brother-cups-wrapper-extra - these are the cups drivers for your printer.
brother-lpr-drivers-extra -  these are the lpr drivers.

You should try the cups first, if they don't work, try the lpr.
If you need assistance in installing and/or configuring, we are here :D

cheers;

---

