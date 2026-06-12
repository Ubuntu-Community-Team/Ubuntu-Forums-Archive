---
title: "vmware player 4.0.4"
date: 2012-06-15
forum: General Help
---

### Post by zylden on 2012-06-15
Hi
I just updated my vmware player from 4.0.3 to 4.0.4 and now I cant run it anymore. It says that /lib/modules/preferred/build/include/linux/version.h in the error log. Now I have looked around online and can only find solutions for upgrading from 4.0.2 to 4.0.3 which does not seem to work on this as I get an error saying:
Sorry, this script is only for VMWare WorkStation 8.0.2 or VMWare Player 4.0.4. Exiting
when i run the patch I found online.
Anyone found a solution for this?
Thanx
SOLVED - the patch does work but you have to delete /usr/lib/vmware/modules/source/.patched

---

### Post by Adrian98 on 2012-06-15
wow , thanks for the ultimate solution! Even I had the similar problem, though Now I made it solved!

---

