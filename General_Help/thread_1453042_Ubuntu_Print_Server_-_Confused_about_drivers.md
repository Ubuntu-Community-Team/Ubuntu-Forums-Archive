---
title: "Ubuntu Print Server - Confused about drivers"
date: 2010-04-12
forum: General Help
---

### Post by adam.ec on 2010-04-12
Hi Folks,
 
I have a small server running in our home-based office with Ubuntu 8.04. At the moment it is just set up as a Samba file server but I wanted to connect a HP F380 all-in-one printer to it.
 
Two questions about this:
 
When I print to this printer (if I can get it to work) is the printing controlled from the windows client on the network or from the driver installed on the server? I ask because Ubuntu's previous performance at printing to this printer has been far from perfect. Print quality was very poor, particulary with graphics. When a Windows machine prints to it the quality was always quite impressive, so if the Windows driver is providing the control presumably I can count on getting the same quality as though the Ubuntu server doesn't even exist.
 
Secondly, is there any way to use the scanner on this device as well? Again, I'm not sure of how drivers are organised in this respect.
 
I'd much prefer to keep this unit running Ubuntu but if the print quality is poor then I will have to switch to MS Server 2003.... something I'd rather never have to do.
 
Thanks

---

### Post by dcstar on 2010-04-13
> **adam.ec said:**
> Hi Folks,
 
I have a small server running in our home-based office with Ubuntu 8.04. At the moment it is just set up as a Samba file server but I wanted to connect a HP F380 all-in-one printer to it.
.......

AFAIK printing from an external device uses that device's drivers - the printer server just passes the job to the printer.

I seriously doubt you will get Remote Scanning going, but you can try.

---

### Post by adam.ec on 2010-04-13
Thank you dcstar. I'll get the printer up and running first. Wish me much more luck with the scanner and if I can get it going I will post back.

---

