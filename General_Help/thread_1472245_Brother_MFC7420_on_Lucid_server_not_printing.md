---
title: "Brother MFC7420 on Lucid server not printing"
date: 2010-05-04
forum: General Help
---

### Post by Leppie on 2010-05-04
i installed the drivers from the brother website which seemed to go fine.
when i go into the cups admin page, i can see the printer listed but when i send a test page to the device nothing happens. the job remains in the queue as processing.
there's no firewall active and i've set apparmor to complain mode for cups (a brother tip).

---

### Post by gandalf2000 on 2010-05-15
I had the same issue and after banging around for awhile found a solution.  If you go to System> Administration> Printing and double click your printer the "Printer Properties" GUI will come up.  In the Device URI box of the "Settings" menu make sure that the network address is there.  Mine had the printer name between the "lpd://NETWORK ADDRESS/binary_P1"  After I changed the printer name to network address it was fixed.

---

