---
title: "Backup software"
date: 2009-09-18
forum: General Help
---

### Post by mike67114 on 2009-09-18
What software would you recommend to backup a single 2-user computer? 
i will be backing up to a USB thumb drive. I am using 9.04 on a Dell AMD64 .

Thanks.

---

### Post by ded3d44 on 2009-09-18
I would recommend rSync. It is a bit hard to setup, but the great thing is it does an incremental backup. 

[http://www.samba.org/rsync/](http://www.samba.org/rsync/)

You could using something like this:
```

rsync -a --delete your-source your-destination

```

Kind regards,
Bram

---

### Post by boonieman on 2009-09-18
**[Back in Time 0.9.26]("http://www.getdeb.net/release.php?id=4757")**

from [GetDeb - Jaunty (32 bits)]("http://www.google.co.th/reader/view/feed/http%3A%2F%2Fwww.getdeb.net%2Frss.php%3Fdistro_id%3D13?hl=en")  



Back In Time is a framework for rsync, diff and cron for the purpose of taking snapshots and backups of specified folders. It minimizes disk space use by taking a snapshot only if the directory has been changed, and hard links for unmodified files if it has. The user can schedule regular backups using cron.

---

