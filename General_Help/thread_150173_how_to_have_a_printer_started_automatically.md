---
title: "how to have a printer started automatically ?"
date: 2006-03-25
forum: General Help
---

### Post by edoardo on 2006-03-25
I'm running ubuntu/kubuntu 510 fully updated, with kde 351.

I have a local HP deskjet940c usb printer also shared with samba and cups.

The problem I have : I neded to START the printer from the kde peripherals settings, every time i start the pc, otherwise print jobs, both local and remote, are held in a queue.

how can i have the printer start automatically on boot ?

from what i see, at runlevel 2, all of samba,cups and hplip are started.
but this is the /etc/cups/printers.conf content:

<DefaultPrinter k3ubuHP840C>
Info HP DeskJet 840C
Location 
DeviceURI usb://HP/DeskJet%20940C?serial=HU1AP6R060BH
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

that 'idle' may be th problem, is it ?

---

