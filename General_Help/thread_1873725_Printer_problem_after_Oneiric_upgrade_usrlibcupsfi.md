---
title: "Printer problem after Oneiric upgrade: /usr/lib/cups/filter/gstoraster failed"
date: 2011-11-01
forum: General Help
---

### Post by sharky6000 on 2011-11-01
Hello all,

I've recently upgraded to Oneiric (from Natty). All went smoothly, except one thing. My Lexmarx Interpret S405 printer no longer works It is recognized and I can add/delete it, but when I go to print it fails and I get a "/usr/lib/cups/filter/gstoraster failed" error message.

I've spent some time trying to figure out what the problem is. Here's what I've done:

- purged the printer driver packages, reinstalled old driver packages
- purged the printer driver packages, reinstalled new driver packages
- purged and re-installed cups
- purged and re-installed ghostscript and ghostscript-cups

I also tried turning CUPS onto debug mode in the hopes that a more detailed error message would appear. The only useful info I got was that gstoraster stopped with status 13. I can provide the log file details if will help.

I saw that there were updates to the cups packages earlier today and hoped that the upgrade may solve the problem, but it hasn't.

Anybody know what may be the trouble or any suggestions on what more I can try?

Thanks in advance,
Marc

---

### Post by lisati on 2011-11-01
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=1873716](http://ubuntuforums.org/showthread.php?t=1873716)

---

