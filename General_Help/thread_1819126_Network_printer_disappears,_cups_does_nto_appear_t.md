---
title: "Network printer disappears, cups does nto appear to start"
date: 2011-08-05
forum: General Help
---

### Post by bharath272 on 2011-08-05
Hello,

I am on Ubuntu 10.04. I had a network printer added, but suddenly now the printer seems to have disappeared. What's more, System->Administration->Printing doesn't allow me to add a new printer.

The System->Admin.->Printing troubleshoot said the following:
"The CUPS print spooler does not appear to be running. To correct this, choose System->Administration->Services from the main menu and look for 'cups'". System->Admin.->Services does not exist. Searching on the net led me to believe that 
/etc/init.d/cups start
would start cups for me, but that does not seem to be happening. 
Any ideas?

Thanks.

---

### Post by bharath272 on 2011-08-05
Okay, seems to be fixed; it seems for some reason installing the xpdf-utils uninstalled cups. At least reinstalling cups also removed xpdf-utils. I am not sure I understand why this must be the case though....

---

