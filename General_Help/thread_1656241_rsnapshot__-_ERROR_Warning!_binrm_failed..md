---
title: "rsnapshot  - ERROR: Warning! /bin/rm failed."
date: 2010-12-30
forum: General Help
---

### Post by dfro on 2010-12-30
Can anyone help me with this problem?

Rsnapshot is aborting with these error messages:

[30/Dec/2010:16:12:31] echo 1292 > /home/user/log/rsnapshot.pid
[30/Dec/2010:16:12:31] /bin/rm -rf /media/backup/rsnapshots/hourly.5/
[30/Dec/2010:16:12:31] /usr/bin/rsnapshot hourly: ERROR: Warning! /bin/rm failed.
[30/Dec/2010:16:12:31] /usr/bin/rsnapshot hourly: ERROR: Error! rm_rf("/media/backup/rsnapshots/hourly.5/")
[30/Dec/2010:16:12:31] /usr/bin/logger -i -p user.err -t rsnapshot /usr/bin/rsnapshot hourly: ERROR: Error! rm_rf("/media/backup/rsnapshots/hourly.5/")
[30/Dec/2010:16:12:31] rm -f /home/user/log/rsnapshot.pid

Thanks,
Dave

---

### Post by dcstar on 2010-12-31
> **dfro said:**
> Can anyone help me with this problem?

Rsnapshot is aborting with these error messages:

[30/Dec/2010:16:12:31] echo 1292 > /home/user/log/rsnapshot.pid
[30/Dec/2010:16:12:31] /bin/rm -rf /media/backup/rsnapshots/hourly.5/
[30/Dec/2010:16:12:31] /usr/bin/rsnapshot hourly: ERROR: Warning! /bin/rm failed.
[30/Dec/2010:16:12:31] /usr/bin/rsnapshot hourly: ERROR: Error! rm_rf("/media/backup/rsnapshots/hourly.5/")
[30/Dec/2010:16:12:31] /usr/bin/logger -i -p user.err -t rsnapshot /usr/bin/rsnapshot hourly: ERROR: Error! rm_rf("/media/backup/rsnapshots/hourly.5/")
[30/Dec/2010:16:12:31] rm -f /home/user/log/rsnapshot.pid

Thanks,
Dave

[LIST=1]
[*]Either the account running that does not have permissions to delete that folder; or
[*]That folder does not exist; or
[*]/bin/rm does not exist.
[/LIST]

---

### Post by ajfda on 2011-07-01
Hello,

An other reason to rm failed is , the disk is in read only mode.

A+

---

