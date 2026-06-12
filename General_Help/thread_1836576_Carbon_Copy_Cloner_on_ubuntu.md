---
title: "Carbon Copy Cloner on ubuntu?"
date: 2011-08-31
forum: General Help
---

### Post by ahso4271 on 2011-08-31
Hi
anything alike Carbon Copy Cloner ( from OSX ) for Linux?
Thanks

---

### Post by dino99 on 2011-08-31
CCC is just a fancy front-end gui for rsync. I'm not sure if there is an equivalent for linux, but if you don't mind the command line, you can do what you want there:

rsync -a -x / /media/backupdisk/

Replace /media/backupdisk/ with whatever mount point your backup disk is attached to.

If you want the backup disk to be an exact copy, add the --delete flag:

rsync -a -x --delete / /media/backupdisk/

---

### Post by ahso4271 on 2011-08-31
Cool thanks.

---

