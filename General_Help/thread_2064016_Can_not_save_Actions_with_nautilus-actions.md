---
title: "Can not save Actions with nautilus-actions"
date: 2012-09-28
forum: General Help
---

### Post by tomtom12 on 2012-09-28
Suddenly, I can not edit existing or save new actions  using  Nautilus-actions

Maybe permission issue but I do not know where Nact stores the actions?  I already chmod 775 .config/nautilus-actions  but there seem no actions in that folder and indeed, it did not help.

---

### Post by tomtom12 on 2012-10-01
Upgrade to 3.2.2... Still can not switch off from read-only...

---

### Post by tomtom12 on 2012-10-03
Ok, found it myself....

Nautilius Actions stores it actions in :  ~/.local/share/file-manager/actions

For some reason that folder was owned by root !  chown and it worked again )

---

