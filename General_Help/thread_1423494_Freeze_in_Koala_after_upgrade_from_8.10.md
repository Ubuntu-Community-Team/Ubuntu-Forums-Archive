---
title: "Freeze in Koala after upgrade from 8.10"
date: 2010-03-06
forum: General Help
---

### Post by jbussoli on 2010-03-06
I've been running a fileserver / media box for years now. First under fedora and now for two years under ubuntu. 

I run Boxee these days but used to be a mythtv user. The hardware I have was upgraded with I switched to Ubuntiu two years ago as well.

After resisting the upgrade "itch" for the past year a new version of Boxee came out this January which led me into an upgrade to Koala which was a brilliantly simple experience until ...... My system would begin freezing requiring a hard reboot. Additionally, it would take my network down!! I couldn't access the internet from other machines while ubuntu was locked up.

I have scoured the forum and google for answers on this to no avail.

Since the initial freezes I have done a fresh install of 9.10 but the problem persists. I have looked for rootkits, changed nvidia drivers, removed compiz all changes that have not yeilded sustained uptime. Some days the box will stay up for a day others it will last 10 minutes.

Can anyone here guide me into the light? 

The following is a syslog dump of the freeze today when it crashed at 8:17. The crash is always preceded by an hourly cron task. I don't have any cron jobs created on this box though!

The next event is me pressing reset at 8:17.

```

Mar  6 08:04:45 harvey-server anacron[8108]: Job `cron.daily' terminated
Mar  6 08:04:45 harvey-server anacron[8108]: Normal exit (1 job run)
Mar  6 08:17:01 harvey-server CRON[8828]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  6 08:39:18 harvey-server kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.

```

---

