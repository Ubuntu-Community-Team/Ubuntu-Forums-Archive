---
title: "&quot;~&quot; files - and how to prevent them"
date: 2009-09-25
forum: General Help
---

### Post by AeroCross on 2009-09-25
Good day everyone - small question here.

I have an Ubuntu installation on a ext4 partition, and all my documents are in another hard drive - NTFS - which is also accessed from Windows. I don't want the "~" files to appear when I'm doing anything in that drive (files like "note.txt~"). I read somewhere that these are backup files automatically made by linux. Is that true? Can I disable it?

---

### Post by jerome1232 on 2009-09-25
More specifically they are backup files created by gedit and also vim, probably other text editors as well, at any rate in gedit you can disable it under the preferences menu.

---

### Post by drs305 on 2009-09-25
From the terminal, to disable gedit backups:
```

gconftool-2 -s --type bool /apps/gedit-2/preferences/editor/save/create_backup_copy 'false'

```
Yeah, I know, running a terminal command for a GUI app is odd....  ;-)

---

### Post by AeroCross on 2009-09-25
Oh my, worked like a charm. If there's any other program that does this, it's just great.

Thanks a lot!

---

### Post by Simian Man on 2009-09-25
> **jerome1232 said:**
> More specifically they are backup files created by gedit and also vim

vim does not do this!!!

Backups are for n00b editors like emacs :).

---

### Post by jerome1232 on 2009-09-25
Your right vim doesn't!

For some reason I thought it did. :p

---

