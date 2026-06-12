---
title: "Network printer will not connect"
date: 2012-07-09
forum: General Help
---

### Post by shamusl on 2012-07-09
My Konica Minolta C-203 won't connect. It's one of those big business printers which has linux drivers and lists compatablity. I installed the PPD file after Ubuntu failed to automatically select the correct driver from the database.

It can be reached from my network at 192.168.0.255, but the system doesn't seem to demand this.

Any ideas?

---

### Post by drdos2006 on 2012-07-09
You are not the only one having problems. Check this thread and the threads within.

[http://ubuntuforums.org/showthread.php?t=2020637](http://ubuntuforums.org/showthread.php?t=2020637)

regards

---

### Post by efflandt on 2012-07-09
Curious what you mean by "installed the PPD file".  An installation script might not work properly in Ubuntu.  Although, when I tried to use one for Lexmark maybe I forgot to use sudo.

Typically when  select to add a printer and select "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect" (which most print servers support), enter the IP of the printer and it cannot find a driver, you point it to the PPD file for that printer, which should then allow you to select your printer.  That is all I had to do for my Lexmark C543d color laser before there was support for it in Ubuntu.  Although before that I found that it worked with a driver Ubuntu had from an older C534.

Many years ago when I was trying to print something from my Linux laptop at a Kinkos Copy Center (before they were FedEx Office) on a parallel port, I could not find any Xerox print drivers.  But I figured that most business printers did postscript, so I configured it to print generic level 2 postscript and it simply worked.

---

### Post by shamusl on 2012-07-13
When I clicked Printers -> add printer -> Network printer

There's an option to add a PPD file on the page that you can choose from already available drivers. I added the PPD file from the Konica-Minolta Site that supports the printer, but its a slightly different model number.

> **efflandt said:**
> Curious what you mean by "installed the PPD file".  An installation script might not work properly in Ubuntu.  Although, when I tried to use one for Lexmark maybe I forgot to use sudo.

Typically when  select to add a printer and select "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect" (which most print servers support), enter the IP of the printer and it cannot find a driver, you point it to the PPD file for that printer, which should then allow you to select your printer.  That is all I had to do for my Lexmark C543d color laser before there was support for it in Ubuntu.  Although before that I found that it worked with a driver Ubuntu had from an older C534.

Many years ago when I was trying to print something from my Linux laptop at a Kinkos Copy Center (before they were FedEx Office) on a parallel port, I could not find any Xerox print drivers.  But I figured that most business printers did postscript, so I configured it to print generic level 2 postscript and it simply worked.

---

