---
title: "WINE Uninstall Question"
date: 2011-01-25
forum: General Help
---

### Post by MikeyDL on 2011-01-25
I have WINE installed on my system and loaded up MS Office 2007.  Having problems with office and when I try to uninstall with the WINE uninstall app it seems to hang.  Can I uninstall wine and start fresh with WINE settings, etc to clean up?

---

### Post by Smart Viking on 2011-01-25
```
sudo apt-get purge wine && sudo apt-get install wine
```
should give you a fresh start.

---

### Post by ajgreeny on 2011-01-25
I suspect you will also need to delete the **~/.wine** folder in your home as well.  If you have other apps installed in wine along with Office, just search for all the Office subfolders of **~/.wine** and just delete them, but if you had wine for Office only, delete the whole of the **~/.wine** folder.

---

### Post by MikeyDL on 2011-01-25
Thanks! 

Going to do both suggestions :)

---

### Post by drewsus on 2011-01-25
I dont think Smart Viking's suggestion is even required. Just ajgreeny's.

---

