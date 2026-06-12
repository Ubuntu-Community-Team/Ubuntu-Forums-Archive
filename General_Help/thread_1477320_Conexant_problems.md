---
title: "Conexant problems"
date: 2010-05-08
forum: General Help
---

### Post by Xemnova on 2010-05-08
Hello. My cousin has been helping me with ubuntu and getting used to it but for a lot of different things i keep getting a conexant problems. it will say :

Setting up conexant (192-1ubuntu-1) ...
/var/lib/dpkg/info/conexant.postinst: 40: update-modules: not found
dpkg: error processing conexant (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 conexant
E: Sub-process /usr/bin/dpkg returned an error code (1)

can someone tell me what this means and how to fix it? it messes up a lot of things i've tried to do and shows up in almost every terminal command i've done updating my computer and such.

---

### Post by gmargo on 2010-05-08
What Ubuntu version are you running?  The **update-modules** command only existed in the 8.04 Hardy and 8.10 Intrepid, and was removed by 9.04 Jaunty.  It was from the **module-init-tools** package.

---

