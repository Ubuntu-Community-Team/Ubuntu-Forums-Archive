---
title: "Filenames on discs listed as &quot;???????&quot;"
date: 2006-04-07
forum: General Help
---

### Post by UBOW on 2006-04-07
As the title says, the filenames on my DVD-R's (data, not video) are not listing correctly but rather as "???????" (without the quotes).

The files themselves seem to work fine and can be selected and executed without issue, at least for the few cases that I've tried.

Also, I've examined these discs under Windows and they read fine, as they always have, so the problem is with my Ubuntu (both Gnome and KDE variants) rather than the discs.

Any suggestions?

---

### Post by IYY on 2006-04-07
Are the filenames in English or some other language.

---

### Post by Internight on 2006-04-07
Do you used Automatix and checked "Eject CD from drive"? This puts dev.cdrom.lock=0 line into /etc/sysctl.conf file and this caused me some similar trouble too. So either try unmounting your drive by hand before changing CD or remove that line.

---

### Post by UBOW on 2006-04-10
Thanks to both for your responses. Rebooted into Ubuntu for the first time in several days and the problem seems to have disappeared. Don't have a clue why (I changed no settings or uninstalled/reinstalled anything). 

Many eyes make shallow bugs indeed...

Still, the problem is gone for now so I'm not complaining :)

---

