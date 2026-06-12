---
title: "Unable to disable 'gnome session auto-save'"
date: 2009-11-13
forum: General Help
---

### Post by emigrant on 2009-11-13
hi all,
i enabled gnome-session auto save through gconf-editor.
and then i disabled it.
but still the session gets saved and upon relogin the prevous session is restored.

how to disable this.

thank you very much for your help.

---

### Post by emigrant on 2009-11-13
one more thing:
its restoring not the previuos session, but the session from which i enabled 'auto save'.

---

### Post by ajgreeny on 2009-11-13
Rename the hidden ~/.nautlius folder in your home and it should stop reloading the session it does now.  Logout and in again to check.

---

