---
title: "Please help with Printer"
date: 2010-12-15
forum: General Help
---

### Post by AmazonasGrun on 2010-12-15
I'm new to Linux and still just getting acquainted and getting everything sorted on my dell inspiron 1000.  Yesterday, I was able to print to my Epson stylus photo r200, and I was even able to share it and send a print job over my local network from a windows client.  Today, the printer is no longer visible from the laptop.  When I try to print, the printer does not even appear in the print window.  I hit help->troublshoot, and it's telling me that the CUPS spooler does not appear to be running.  It suggests that I go to System->Adminstration->services and look for the CUPS service.  However, "services" does not appear in the "system" menu.

How do I get my printer back on line?  I've tried rebooting, and shutting down the printer and starting it again to no avail.

I've got Ubuntu 10.10.

Thanks!

---

### Post by AmazonasGrun on 2010-12-15
I tried opening a terminal, and typing "sudo service cups start". The response: "Job failed to start"

---

### Post by AmazonasGrun on 2010-12-15
Ok, after doing more searching on the Forum, I reloaded CUPS with

sudo apt-get install --reinstall cups
All is well!

But, why was that necessary?  What caused CUPS to stop working?

---

