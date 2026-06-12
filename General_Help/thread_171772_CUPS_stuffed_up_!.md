---
title: "CUPS stuffed up !"
date: 2006-05-07
forum: General Help
---

### Post by tuxy on 2006-05-07
Accidently I have removed CUPS from my pc. If i do apt-get install cupsys, now I get this message saying:
-----------------
grep: /etc/cups/cupsd.conf: No such file or directory
Your /etc/cups/cupsd.conf appears to have been manually edited. cupsys.postinst won't touch it.
update-rc.d: /etc/init.d/cupsys: file does not exist
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
------------

How to reinstall the CUPSYS now?

---

