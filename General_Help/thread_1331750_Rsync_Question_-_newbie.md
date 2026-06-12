---
title: "Rsync Question - newbie"
date: 2009-11-19
forum: General Help
---

### Post by Quarkrad on 2009-11-19
I have setup a rsync session that copies the contents of one folder /home/dad/xxx/ to another folder on a different internal HD  /media/sb1/xxx/ via GAdminRsync.  (Through this forum I got a bit clever and run it when my shuts down).  It all works great but I wondering - is everything copied or only changes?

---

### Post by renkinjutsu on 2009-11-19
with rsync, usually, only changes are copied. But in some cases, if the --delete option is used, rsync'll delete files in your destination that isn't in your source.

---

### Post by geurt on 2009-11-19
please run the command:
```
man rsync
```

and look at the rsync options..a lot of options to keep directories and files synchronized.

---

### Post by Quarkrad on 2009-11-21
many thanks

---

