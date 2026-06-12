---
title: "iprint problems"
date: 2012-02-02
forum: General Help
---

### Post by keyanm on 2012-02-02
Hello,

I have installed the latest 64 bit iprint on ubuntu through alien. 
I can print to a printer using
iprntcmd -p ipp://ptr.blah.com/ipp/PXXX-BW job.ps
which asks me for credentials and prints successfully.
I can also add a printer using iprntcmd -a, and it will show up in the system printers.
However, I cannot print using the system printer, and I get the error:

Idle - /usr/lib/cups/backend/iprint failed

in the printer state line, and the job will be held in the queue indefinitely, no credentials will be asked.

I have even tried changing the Listen localhost:631 in cupsd.conf to *:631 with no avail.
Any help would be highly appreciated as I cannot figure out what's wrong, and it has taken many many hours!

---

