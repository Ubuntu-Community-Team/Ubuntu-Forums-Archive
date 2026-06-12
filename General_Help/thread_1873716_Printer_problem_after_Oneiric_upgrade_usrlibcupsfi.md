---
title: "Printer problem after Oneiric upgrade: /usr/lib/cups/filter/gstoraster failed"
date: 2011-11-01
forum: General Help
---

### Post by sharky6000 on 2011-11-01
Hello all, 

I've recently upgraded to Oneiric (from Natty). All went smoothly, except one thing. My Lexmarx Interpret S405 printer no longer works :( It is recognized and I can add/delete it, but when I go to print it fails and I get a "/usr/lib/cups/filter/gstoraster failed" error message.

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

### Post by sharky6000 on 2011-11-01
Oops, I meant to put this into the General Help forum. I'll repost there. Can someone please delete this one? Thanks.

---

### Post by lisati on 2011-11-01
*Thread moved to **General Help**.*

---

### Post by waltsullivan on 2011-12-14
There are no links to the moved thread in your post. Is this on purpose? All I can find are posts saying "...moved to General Help".

---

