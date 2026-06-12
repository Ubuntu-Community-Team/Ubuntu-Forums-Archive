---
title: "LPD and D-Link Print Server"
date: 2009-09-15
forum: General Help
---

### Post by hofstra14 on 2009-09-15
I am trying to configure an HP Photosmart 1115 printer through a D-Link network print server.  I have tried to configure it as an LPD printer by entering the IP address of the print server and then selecting the driver.  When I try to print a test page I get the message 'LPD failed'.
 
I also tried IPS by entering the name of the print server, but that does not seem to work either.
 
Any ideas?

---

### Post by hofstra14 on 2009-09-15
OK, figured it out;  you need to use the IP address plus the Printer Name as shown on the D-Link print server setup page.

lpd://192.168.1.251/PS-25F683-P1

---

