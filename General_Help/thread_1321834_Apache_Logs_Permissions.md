---
title: "Apache Logs Permissions"
date: 2009-11-10
forum: General Help
---

### Post by ericinwisconsin on 2009-11-10
Not sure where to get help with this one, but maybe someone can point me in the right direction...

I have logs in Apache for my various websites. Each website has its own combined log.

On one site (and only one site), the permissions change on the log file. Not sure if it's Apache, logrotate, or some other process causing the problem. The group changes from utmp to adm and the permissions change from 664 to 640. Maybe it's happening during the cron job to rotate files; I'm not sure.

Has anyone else encountered this problem? Or can someone suggest where to go for assistance on this?

Thanks!

---

