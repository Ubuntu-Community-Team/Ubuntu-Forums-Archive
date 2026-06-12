---
title: "Ubuntu 10.04 Printing files takes ages!"
date: 2010-05-23
forum: General Help
---

### Post by socceroos on 2010-05-23
When printing web pages or PDF files in Ubuntu 10.04 to a network printer using CUPS, files are blown out to huge sizes - over 200Mb for a 30Mb PDF document and over 70Mb for a simple web page with 6 images and some text.

Its holding up everyone else in our office who, through Windows XP are printing the same files in about a 20th of the time it takes Ubuntu+CUPS.

I have tried printing directly to the printer, printing through the Win2003 PDC share, printing with LPR (which coincidentally generates a bit smaller ps file) and printing with Adobe Reader instead of evince - all to no avail.

---

### Post by oldwismn on 2010-05-25
I was also experiencing absurdly long print times.  It took almost 15 minutes to print a 5 page HTML email from Evolution.  The problem started when I updated to 10.04.

I changed the print driver (from Laserjet 1320 Postscript to Laserjet 1320 hpijs 3.10.2).  This solved my problem.  The same email prints in less than a minute.

---

### Post by ralph0015 on 2010-06-03
Thank you, thank you thank you!!!!!  Just needed to switch to the driver mentioned here and all is now good with .pdf printing.

---

### Post by 3L33T on 2010-07-08
I had sorta different printing issue.

Ubuntu Desktop 10.04 LTS.

Whenever I print from ** any ** application (Firefox, Zimbra, OO suite, etc) to  any jetdirect print server connected printer there is atleast about 5-10 seconds delay before the File --> Print window to come up with the list of printers to choose from.   Does this  mean Lucid is checking with CUPS then and only then for the list of printers?  This hidden feature has become a bit annoying ;)

I fixed this *delay* by following oldwismn post above...changing the driver to xxxhpijs xxxxx.  Now, no more delay.  Hope this helps someone.

---

