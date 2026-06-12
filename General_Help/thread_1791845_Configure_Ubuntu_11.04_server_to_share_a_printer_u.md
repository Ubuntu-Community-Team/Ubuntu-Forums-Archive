---
title: "Configure Ubuntu 11.04 server to share a printer using terminal (not GUI)"
date: 2011-06-27
forum: General Help
---

### Post by bpb_21 on 2011-06-27
I've been searching for something on this topic and haven't come across what I need.
I've got an Ubuntu Server 11.04 running and the primary use of it is to store backup files using Deja Dup, connecting through SSH using shared key (no passwords) authentication.  This works on the LAN and WAN, which is what I want.

I also want to set up an HP Officejet 5610 MFD to be shared on the LAN only, for printing and scanning.  The server obviously doesn't have a GUI.

I've searched and come up with some near misses, but everywhere I try it seems someone is using a GUI on the system serving the printer.
See:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)
[https://help.ubuntu.com/community/PDFPrinting?action=show&redirect=PrintToPDF](https://help.ubuntu.com/community/PDFPrinting?action=show&redirect=PrintToPDF)
[http://blog.joeb454.com/2008/09/printer-sharing-with-ubuntu-server/](http://blog.joeb454.com/2008/09/printer-sharing-with-ubuntu-server/)
[http://linux.about.com/od/ubusrv_doc/a/ubusg31t01.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg31t01.htm)

What I'd really like would be a post like the following one.  It seems to be what I'm looking for, but it is from 2006 using Ubuntu 6.## and that build ran on cupsys rather than cupsd if I read correctly.  I haven't found an updated guide/post like the one below.  Does anyone know of any information that might help, such as an updated post like the one below?

[http://ubuntuforums.org/showthread.php?t=240282](http://ubuntuforums.org/showthread.php?t=240282)

---

### Post by seawolf167 on 2011-06-27
I'm not sure about the CLI printer setup, but since you are running headless, you may want to take a look at [Webmin]("http://doxfer.webmin.com/Webmin/WebHome"). The printer administration is covered on [this page]("http://doxfer.webmin.com/Webmin/PrinterAdministration").

---

### Post by bpb_21 on 2011-07-02
> **seawolf167 said:**
> I'm not sure about the CLI printer setup, but since you are running headless, you may want to take a look at [Webmin]("http://doxfer.webmin.com/Webmin/WebHome"). The printer administration is covered on [this page]("http://doxfer.webmin.com/Webmin/PrinterAdministration").

Thanks for the tip, but I can't even get it to print from the server to the (directly attached) printer.  The server "sees" the printer, the error_log file (set to debug2) says the print job was sent successfully, the /etc/cups/printer.conf file has the printer listed correctly (as far as I can tell), but the printer doesn't do anything.  (It is powered on and connected.)  No actual "error" messages whatsoever.

So as of right now I'm looking at Windows again.  Dang.  So close.

---

