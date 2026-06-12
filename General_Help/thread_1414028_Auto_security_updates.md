---
title: "Auto security updates"
date: 2010-02-23
forum: General Help
---

### Post by Simoo on 2010-02-23
Hi,

I need Ubuntu to download and install security updates automatically but I need it to happen unaided during the early hours of the morning. Manual upgrades will be carried out every month or so.

I made these entries in root's crontab:

```
0 3 * * * /usr/bin/aptitude -y update 2>&1 >> /var/log/auto_update.log
```

```
5 3 * * * /usr/bin/aptitude -y safe-upgrade 2>&1 >> /var/log/auto_update.log
```

syslog shows that the commands are being run but /var/log/auto_update.log ends with:

"initializing package states..."

and nothing is upgraded.

Help would be much appreciated, thank you.

---

