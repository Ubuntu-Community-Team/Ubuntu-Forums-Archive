---
title: "Open Kate with the file browser panel closed?"
date: 2006-02-21
forum: General Help
---

### Post by vayu on 2006-02-21
I want to open kate and have the left pane with the file browserclosed by default.  I have tried closing it then saving my session, but when I reopen kate, the left pane file browser is open again.

---

### Post by Jucato on 2006-02-21
Go to Windows > Tool Views > Hide [whatever you want to hide]
Save session, exit
Next time you open Kate, whatever is closed will be closed, whatever is open will be opened.

---

### Post by vayu on 2006-02-21
Turns out that for some reason ~/.kde/share/apps/kate and all folders and files below it were owned by root.  chown'ed to my user and all is now saved when I save session.

---

