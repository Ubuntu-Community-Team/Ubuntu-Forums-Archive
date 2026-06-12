---
title: "Setting Up Printers From The Command Line"
date: 2011-03-14
forum: General Help
---

### Post by msp3k on 2011-03-14
Hi gurus,

I can set up a printer using the System > Administration > Printing (i.e. /usr/bin/python /usr/share/system-config-printer/*).

That's all nice and fine -- until I take into consideration that there are currently 45 machines that need to have this printer set up on them.  Then the GUI interface isn't so cool anymore.

I can set up a printer just fine from the command line via the lpadmin command, but I have no idea where the system-config-printer got the PPD file from.

Does anyone know how to backtrack a PPD file installed in /etc/cups/ppd/ to it's origins?  I have checked in /usr/share/ppd/, but there is nothing there for this model printer -- that I can see anyway.

---

### Post by marshag63 on 2011-03-14
Perhaps

/usr/share/foomatic/db/source/driver

MDG

---

