---
title: "Get printer properties via the command line"
date: 2011-02-10
forum: General Help
---

### Post by awp2513_ on 2011-02-10
Hi,

When I configure a printer via the command line, I can specify the driver to use (lpadmin ... -m ...).

Is there a way to see what driver I've selected from the command line after I've configured the printer? No options I've seen for lpadmin, lpstat, etc. have provided me with this information, 

The information I'm looking for is displayed in the Printer (setup) dialog in Gnome. Where does it get its information from?

Thanks!

---

### Post by anglican on 2011-02-11
> **awp2513_ said:**
> Hi,

When I configure a printer via the command line, I can specify the driver to use (lpadmin ... -m ...).

Is there a way to see what driver I've selected from the command line after I've configured the printer? No options I've seen for lpadmin, lpstat, etc. have provided me with this information, 

The information I'm looking for is displayed in the Printer (setup) dialog in Gnome. Where does it get its information from?

Thanks!```
sudo less /etc/cups/printers.conf
```;)

H

---

