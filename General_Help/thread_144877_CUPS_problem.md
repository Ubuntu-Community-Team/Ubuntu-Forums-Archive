---
title: "CUPS problem ?"
date: 2006-03-15
forum: General Help
---

### Post by MaaSTaaR on 2006-03-15
Hello ...

when i open System->Administration->Printing it's show for me this error

"CUPS server could not be contacted"


and CUPS's log file is :

I [15/Mar/2006:17:15:55 +0300] Listening to 7f000001:631
I [15/Mar/2006:17:15:55 +0300] Loaded configuration file "/etc/cups/cupsd.conf"
I [15/Mar/2006:17:15:55 +0300] Configured for up to 100 clients.
I [15/Mar/2006:17:15:55 +0300] Allowing up to 100 client connections per host.
I [15/Mar/2006:17:15:55 +0300] Full reload is required.
E [15/Mar/2006:17:15:55 +0300] LoadAllPrinters: Unable to open /etc/cups/printers.conf - No such file or directory
E [15/Mar/2006:17:15:55 +0300] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [15/Mar/2006:17:15:55 +0300] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [15/Mar/2006:17:15:56 +0300] LoadPPDs: No new or changed PPDs...
I [15/Mar/2006:17:15:56 +0300] Full reload complete.
I [15/Mar/2006:18:16:40 +0300] Scheduler shutting down normally.
I [15/Mar/2006:18:29:11 +0300] Listening to 7f000001:631
I [15/Mar/2006:18:29:11 +0300] Loaded configuration file "/etc/cups/cupsd.conf"
I [15/Mar/2006:18:29:11 +0300] Configured for up to 100 clients.
I [15/Mar/2006:18:29:11 +0300] Allowing up to 100 client connections per host.
I [15/Mar/2006:18:29:11 +0300] Full reload is required.
E [15/Mar/2006:18:29:11 +0300] LoadAllPrinters: Unable to open /etc/cups/printers.conf - No such file or directory
E [15/Mar/2006:18:29:11 +0300] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
W [15/Mar/2006:18:29:41 +0300] LoadDevices: Backend did not respond within 30 seconds!
I [15/Mar/2006:18:32:22 +0300] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [15/Mar/2006:18:32:25 +0300] LoadPPDs: Wrote "/etc/cups/ppds.dat", 3692 PPDs...
I [15/Mar/2006:18:32:25 +0300] Full reload complete.
E [15/Mar/2006:18:32:25 +0300] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.


now what should i do ? :-?

---

### Post by noswal on 2006-03-15
Had same problem, did this:

System > Administration > Services   scroll down and enable  printer service (cupsys)

Now try  System > Administration > Printing

---

