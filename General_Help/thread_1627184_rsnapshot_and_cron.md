---
title: "rsnapshot and cron"
date: 2010-11-21
forum: General Help
---

### Post by chris00 on 2010-11-21
Hi,

I am trying to run rsnapshot from cron via root's crontab file (crontab -e). If I run rsnapshot from the command line with sudo it works perfectly, however, if I run it from cron:

```
* * * * *       /usr/bin/rsnapshot hourly >/tmp/crontab.out 2>/tmp/crontab.err
```

This does not work. The crontab.err file shows:

```
----------------------------------------------------------------------------
rsnapshot encountered an error! The program was invoked with these options:
/usr/bin/rsnapshot hourly 
----------------------------------------------------------------------------
ERROR: Could not write lockfile /var/run/rsnapshot.pid: Permission denied
```

Surely this should work if this is root's crontab file since /var/run is owned by root?

Any help is greatly appreciated.

Thanks,
Chris

---

### Post by DaithiF on 2010-11-21
crontab -e edits **your** crontab, not root's.

sudo crontab -e edits root's crontab.  

which are you doing?

---

### Post by chris00 on 2010-11-21
Thank you - I wasn't using sudo so I was editing the wrong crontab. Works perfectly now.

---

