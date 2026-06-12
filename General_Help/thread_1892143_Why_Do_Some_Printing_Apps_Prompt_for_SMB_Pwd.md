---
title: "Why Do Some Printing Apps Prompt for SMB Pwd?"
date: 2011-12-07
forum: General Help
---

### Post by cmnorton on 2011-12-07
I have an SMB printer defined on Ubuntu 10.04. The printer is running on Windows XP Workstation. The SMB definition has the password embedded in its connect string. Evolution and Firefox prompt for a password. Gedit and vim don't. 

Why?

Can I correct this?

If I can correct this, how?

Thanks.
cmn

remove #AuthInfoRequired username,password
from the printer's definition in /etc/cups/printers.conf

---

