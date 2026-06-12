---
title: "Finding printer on XP machine"
date: 2009-07-06
forum: General Help
---

### Post by wetzeldc on 2009-07-06
I'm new to Linux and Ubuntu.  I have a dual boot PC, XP and Ubuntu.  We have a couple other computers, a Vista machine and a 2nd XP machine.  They are networked via Microsoft Windows Network where the 2nd XP machine, called MARY, is the server.  It is hooked up to the printer.  On my dual boot machine, called DCW, when running XP I can find and use the printer.  When running Ubuntu and trying to add a printer via Samba, I get as far as seeing the MARY computer on the network, but then when I click on MARY to find the printer, all the popup windows disappear and I am back at the desktop.  I tried turning off the firwall on MARY, the server, with no change in the results.  
What do I do to get the printer working on Ubuntu?

---

### Post by Jerry N on 2009-07-07
Get to the printer configuration window through
   System >  Administration > Printing
Select New
Get the pull-down menu under "Network Printer"
Select "Windows Printer via SAMBA"
In the box under "SMB Printer" enter the server name and the shared printer name.  (Be sure that the printer is shared on the Windows Server)
In my case, the path to one of my printers is ATHLON3800/LJ1320.

Linux seems to be real dumb when it comes to finding printers on a Windows server although, as you have noted, it finds other Windows shares OK.

Jerry

---

### Post by wetzeldc on 2009-07-07
Thanks for the reply.  I was able to install the printer but it doesn't print.  It may be related to not being able to access the other XP computer at all.  Starting with Places -> Network -> Windows Network -> Mshome -> MARY  -- then when I click on Mary I get the message "Opening Mary"  nothing happens then the error message "Unable to mount location - Failed to retrieve share list from server"
Any ideas on what's going on and fixes?

---

