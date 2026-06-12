---
title: "filesystem"
date: 2009-09-25
forum: General Help
---

### Post by ub007 on 2009-09-25
quick question, answer may take longer :)

when i remount a file system as writable ie mount -o remount, rw /trial,how does the linux os know that  /trial is now writable......trying to work out the internals here...
:confused:

Cheers
David

---

### Post by Liolikas on 2009-09-25
Answer even shorter: simple just write things down in /etc/mtab

---

### Post by ub007 on 2009-09-25
thank you for that info.

so a mount request automatically updates /etc/mtab ,so is it that the kernel keeps polling the mtab file every /second/min... to check what it can write to and what it cant....

---

