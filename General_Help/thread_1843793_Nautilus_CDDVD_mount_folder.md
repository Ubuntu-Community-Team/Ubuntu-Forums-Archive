---
title: "Nautilus CD/DVD mount folder"
date: 2011-09-14
forum: General Help
---

### Post by zidolson on 2011-09-14
Hi,

If you insert a DVD, say JAWS, this gets mounted under /media/JAWS. I would prefer that any inserted DVD always is mounted under /media/cdrom instead. How do I achieve that?

This would make it much easier to handle these under wine. Currently I have to run winecfg each time a new DVD is inserted.

Best regards,

Zid

---

### Post by linux2001 on 2011-09-14
Add new line in /etc/fstab
```
/dev/cdrom              /media/cdrom              udf,iso9660 noauto,owner,kudzu,ro 0 0

```

---

### Post by zidolson on 2011-09-14
Thanks a lot. This solved it. BTW: What does kudzu stand for in your fstab line?

---

