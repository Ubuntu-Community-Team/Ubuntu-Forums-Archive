---
title: "Printing Gotcha"
date: 2010-07-24
forum: General Help
---

### Post by tkoco on 2010-07-24
I needed to get the Ubuntu laptop printing on the Ubuntu desktop printer. Had CUPS fully loaded on both ends. Got the firewall fixed on the desktop for incoming CUPS printing. Even remembered to tell the desktop CUPS server to broadcast the shared printer. But could not get the client laptop to see the desktop printer.
The Fix? So simple I can kick myself. The CUPS server on the laptop needed to have the "Show printers shared by other systems" checked. After checking that and restarting the CUPS server on the laptop, I "Added" a printer using the "Network Printer -> Find Network Printer" and plugged in the IP address of the desktop. It was downhill from there on.:p

---

