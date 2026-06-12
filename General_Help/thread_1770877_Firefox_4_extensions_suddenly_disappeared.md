---
title: "Firefox 4 extensions suddenly disappeared"
date: 2011-05-29
forum: General Help
---

### Post by pickarooney on 2011-05-29
Out of the blue all of my extensions (adblock, google toolbar etc.) have stopped working and are no longer listed in the Add-Ons section of Firefox 4.0.1.

I guess it might be something to do with my profile but am not sure how to repair it or create a new one which will work with add-ons.

Is there a debug option from the command line that might help?

---

### Post by linuxinstalledfromhdd on 2011-05-29
Can you reverse the changes you have made to your system recently?

---

### Post by lovinglinux on 2011-05-29
If you are using *firefox-next* ppa, then is probably because your Firefox has been upgraded to version 5.

Go to the "Help >> About Firefox" and make sure you are still running Firefox 4.0.1.

If the version is indeed 5, then open the Add-on Manager and click "Check for Updates". This should apply compatibility patches.

You could also install the add-ons again, if there are no updates available.

Also make sure you don't have a cloned profile under ~/.mozilla/firefox-4.0 in addition to ~/.mozilla/firefox. Copy the contents of the cloned profile into the default one (make backups first).

---

