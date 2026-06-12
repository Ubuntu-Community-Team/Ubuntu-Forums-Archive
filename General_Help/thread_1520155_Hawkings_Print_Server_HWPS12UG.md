---
title: "Hawkings Print Server HWPS12UG"
date: 2010-06-29
forum: General Help
---

### Post by tom_calthrop on 2010-06-29
Hi All,

I have removed my Windows Print Server in favour of a Hawkings Print Server HWPS12UG (connects 2 USB printers to a wireless network and presents them as network printers). 

I am connected to the same network and running Lucid 10.04

On the print server is a Samsung ML-2010.

I print and it prints perfectly, however Ubuntu then reports an error and pauses the printer. I cannot work out why and my CUPS knowledge could be detailed on a stamp ;)

The job attributes say:

job-printer-state-message : /usr/lib/cups/backend/htp failed
job-printer-state-reason : [u'paused']

The print server does not report any problems when printing from Windows. This leads me to believe that CUPS is awaiting some feedback or receiving feedback that it is reading as an error. So...

1. Has anyone ever seen this before?
2. Can someone give me some commands/workthrough so that I can explore what CUPS is really getting?
3. Can I convince CUPS to ignore this? (noting that the printing is fine).

Many thanks up front for assistance here! 

Tom

---

### Post by tom_calthrop on 2010-06-29
Solved this myself, but wanted to log it for the next person...

The server sets the port to be "lpt2", but Ubuntu wants to read it in this format:

lpd://192.168.1.150/LPT2

Tom

---

