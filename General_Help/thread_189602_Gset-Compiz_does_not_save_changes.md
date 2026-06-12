---
title: "Gset-Compiz does not save changes"
date: 2006-06-05
forum: General Help
---

### Post by MegaBill on 2006-06-05
Exactly as title says.  When I try to modify the compiz settings using gset-compiz, the changes are never saved once the program closes, and nothing operates the way I configured it.  I even tried a sudo gset-compiz, and that didn't work either.  Everything worked fine in the Dapper Beta, but now it isn't.  Any ideas anyone?

---

### Post by MegaBill on 2006-06-05
I'm betting it's a permissions problem, but I can't figure out this thing... if anyone knows another way to configure xgl, or if anyone has a solution to this issue, please let me know.

---

### Post by amonsul on 2006-06-05
I have the same problem!

---

### Post by mhafren on 2006-06-06
Same problem here, somebody please help:)

---

### Post by panurge77 on 2006-06-06
I think gset-compiz will use gconf entries to save your settings, so make sure you're starting compiz with gconf option. Check the gconf-editor apps>compiz the settings should be there. If you can configure it in gconf-editor, then the problem is indeed in gset.

---

