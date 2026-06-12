---
title: "Date &amp; Time stored on shutdown?"
date: 2009-12-30
forum: General Help
---

### Post by pgorillaman on 2009-12-30
Where is the date/time information stored when the system is shutdown?

I have a backup solution that copies the entire root partition. When it is restored, it also restores the date to when the backup was made! I need to exclude the file with the date/time when backing up. I've searched but can't find out where this file is.

---

### Post by pgorillaman on 2009-12-30
bump

---

### Post by pgorillaman on 2009-12-31
bump

---

### Post by dcstar on 2009-12-31
> **pgorillaman said:**
> Where is the date/time information stored when the system is shutdown?

I have a backup solution that copies the entire root partition. When it is restored, it also restores the date to when the backup was made! I need to exclude the file with the date/time when backing up. I've searched but can't find out where this file is.

AFAIK /etc/adjtime
```
man hwclock
```

---

