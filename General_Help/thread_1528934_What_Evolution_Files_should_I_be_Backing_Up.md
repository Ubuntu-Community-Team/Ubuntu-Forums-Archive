---
title: "What Evolution Files should I be Backing Up?"
date: 2010-07-11
forum: General Help
---

### Post by jt867 on 2010-07-11
[SIZE=7][FONT=Arial] [SIZE=2]On Windows XP; I backup my MS Outlook mail client be only backing up a .pst file. What file or files in Evolution do I need to backup that will have all my emails, calendar and contacts like the .pst file from MS Outlook?

Regards,

John...
[/SIZE][/FONT][/SIZE]

---

### Post by ajgreeny on 2010-07-11
There is a hidden folder in your home called .evolution where everything is stored.  To see hidden files and folders hit Ctrl+H in nautilus or go to the View menu.

---

### Post by DZ* on 2010-07-11
There is stuff in both ~/.evolution and ~/.gconf/apps/evolution
and it's not enough to just copy the files.

```
evolution --force-shutdown
gconftool-2 --shutdown
cd
tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution
```

Evolution can make a backup file (File -> Backup Settings), however this method doesn't backup stored passwords.

---

### Post by philinux on 2010-07-11
In evolution File>backup

---

