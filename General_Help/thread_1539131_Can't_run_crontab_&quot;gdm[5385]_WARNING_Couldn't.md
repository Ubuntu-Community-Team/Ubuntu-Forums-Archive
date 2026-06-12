---
title: "Can't run crontab &quot;gdm[5385]: WARNING: Couldn't authenticate user&quot;"
date: 2010-07-26
forum: General Help
---

### Post by poohpeer on 2010-07-26
Hello everyone,

I'm using ubuntu 8.10 server and trying to configure cron to run some perl scripts, but when I edit the crontab (crontab -e) followng errors occur in /var/log/syslog. In spite of this, my new configuration is saved.

```
Jul 26 05:42:13 sofa last message repeated 8 times
Jul 26 05:42:13 sofa crontab[22737]: (alex) BEGIN EDIT (alex)
Jul 26 05:42:14 sofa gdm[5385]: WARNING: Couldn't authenticate user
```Crontab execution fails as well:

```
Jul 26 05:43:01 sofa /usr/sbin/cron[5469]: (alex) RELOAD (crontabs/alex)
Jul 26 05:43:01 sofa gdm[5385]: WARNING: Couldn't authenticate user
Jul 26 05:43:32 sofa last message repeated 20 times
```What could cause such disappointment?

---

