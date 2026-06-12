---
title: "Printing to Canon MP280 on Windows server"
date: 2012-02-25
forum: General Help
---

### Post by timsclips on 2012-02-25
Last week I picked up a Canon MP280 allinone at the local Walmart to replace a 5 yr old allinone that would no longer feed paper.  It was cheap and since I was able to print to the old Canon printer via the windows server I did not think I would have much of an issue printing to the new one.
I am using Ubuntu 11.10 and was happy to see PIXMA MP280 drivers listed when I was going to add the new printer.  I tested the access to the shared printer and it showed I had access.  I tried to print and the printer woke up from "sleep" and went thru a bunch of noises with the carriage but never fed paper or printed.  Doing some research I found a newer driver for linux was available ver 3.4 from Canon's European website.  I tried running the install script but it only recognises local or network printers with an IP address.  I found that I had to download the source driver and then upload the ppd file to get the printer to work.  Not sure if others are struggling with this printer but I thought I would share what I had found.

[http://software.canon-europe.com/software/0040245.asp?model=](http://software.canon-europe.com/software/0040245.asp?model=)

---

