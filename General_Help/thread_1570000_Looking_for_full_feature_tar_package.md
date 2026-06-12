---
title: "Looking for full feature tar package"
date: 2010-09-07
forum: General Help
---

### Post by Skaperen on 2010-09-07
It looks like Ubuntu is using the lame GNU tar that can't handle sockets.  Anyone know of a full featured tar package for Ubuntu?  I know Slackware has it, but it's not clear where that comes from.  I could use the source from Slackware to built it, but I'm wanting to keep all my Ubuntu machines managed through Ubuntu packages if I can.

```
tar: backup/save/servers/archimedes/var/spool/postfix/private/smtp: socket ignored
tar: backup/save/servers/archimedes/var/spool/postfix/private/tlsmgr: socket ignored
tar: backup/save/servers/archimedes/var/spool/postfix/private/trace: socket ignored
tar: backup/save/servers/archimedes/var/spool/postfix/private/uucp: socket ignored
tar: backup/save/servers/archimedes/var/spool/postfix/private/verify: socket ignored
tar: backup/save/servers/archimedes/var/spool/postfix/private/virtual: socket ignored

```

---

### Post by linux-hack on 2010-09-07
If I understand correctly you want to make a tar archive on a distant server ?

---

### Post by Skaperen on 2010-09-07
More like one that is closer.  I already have scripts that do this and process the tarballs.  I'm wanting to migrate that to Ubuntu.

---

### Post by andrew.46 on 2010-09-07
Hi Skaperen,

> **Skaperen said:**
> I know Slackware has it, but it's not clear where that comes from. 

Details of the Slackware tar source and configure options here:

[http://slackware.osuosl.org/slackware-13.1/source/a/tar/](http://slackware.osuosl.org/slackware-13.1/source/a/tar/)

Andrew

---

