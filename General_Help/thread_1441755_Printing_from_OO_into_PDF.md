---
title: "Printing from OO into PDF"
date: 2010-03-29
forum: General Help
---

### Post by camel1cz on 2010-03-29
Hello,

I have a printing problem from OpenOffice since few weeks already.

My printing to PDF (cups pdf printer) and also direct "Export to PDF..." doesn't work anymore.

When I "Export to PDF..." it creates empty PDF file - what's strange, it has correct number of (empty) pages and the PDF has correct Index.

When I print to CUPS PDF printer, it does nothing at all (no notification about new printing job, etc.) In the log:

localhost - - [29/Mar/2010:11:38:15 +0200] "POST / HTTP/1.1" 200 417 CUPS-Get-Printers successful-ok
localhost - - [29/Mar/2010:11:38:15 +0200] "POST / HTTP/1.1" 200 417 CUPS-Get-Classes successful-ok
localhost - - [29/Mar/2010:11:38:15 +0200] "POST / HTTP/1.1" 200 75 CUPS-Get-Default client-error-not-found

Can somebody help?

I use Jaunty with latest updates (cups 1.3.9-17ubuntu, cups-pdf 2.5.0-1ubuntu1, openoffice 1:3.0.1-9ubuntu)

Thanks!

---

