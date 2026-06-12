---
title: "cups does not start"
date: 2006-02-12
forum: General Help
---

### Post by DavidJames on 2006-02-12
Following startup (of 5.10) or whenever I try to start cupsys from the command line I get the follwing entries in the cups log (/var/cups/log/err_log):

I [12/Feb/2006:10:43:25 +0000] Listening to 7f000001:631
I [12/Feb/2006:10:43:25 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [12/Feb/2006:10:43:25 +0000] Configured for up to 100 clients.
I [12/Feb/2006:10:43:25 +0000] Allowing up to 100 client connections per host.
I [12/Feb/2006:10:43:25 +0000] Full reload is required.
W [12/Feb/2006:10:43:55 +0000] LoadDevices: Backend did not respond within 30 seconds!
I [12/Feb/2006:10:46:34 +0000] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [12/Feb/2006:10:46:34 +0000] LoadPPDs: No new or changed PPDs...
I [12/Feb/2006:10:46:34 +0000] Full reload complete.
E [12/Feb/2006:10:46:34 +0000] StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address.

Consequently, I am not able to install a printer. Stangely, on one occasion cups did start and I was able to install a printer (Epson Stylus CX3650) on a usb port and I printed from both Open Office and Gimp. But that seems to have been a one-off.

There are a number of threads about problems with printing, including the failure of cups, but none (or at least those I've found) seem to include the error message that I am getting.

I am a relative newcommer to Linux (just a few months) and am really a point-and-click person, so I want to be able to install printers through System>Administration>Printing.

I have been able to set up most of what I need within ubuntu so as to make my study a Windows-free-zone, but I need to be able to print. Any help would be appreciated.

---

