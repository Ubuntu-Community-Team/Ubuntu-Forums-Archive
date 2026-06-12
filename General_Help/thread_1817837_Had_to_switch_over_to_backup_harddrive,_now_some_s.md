---
title: "Had to switch over to backup harddrive, now some services won't start."
date: 2011-08-03
forum: General Help
---

### Post by CptanPanic on 2011-08-03
I had my main system drive being mirrored, and the drive died, so I switched over to the backup drive.  System boots up fine, but I noticed that some services are not working such as cups and mysql.  When I try to do  "start cups" I simply get "start: Job failed to start", with empty cups logs, and the syslog only says "process  terminated with status 1".  Also I can start cupsd manually and it works, so it is something wrong with initctrl .  This is with 11.04, and the same problem is with mysql.   How can I debug and fix this problem?
Thanks,
CP

---

### Post by CptanPanic on 2011-08-04
No ideas?  Maybe a mod can move this into the server forum, since it is related to server services?
Thanks,
CP

---

