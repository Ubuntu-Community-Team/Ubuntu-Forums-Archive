---
title: "NTP log configuration"
date: 2010-07-08
forum: General Help
---

### Post by derek71 on 2010-07-08
I have NTP installed and running under Ubuntu server 10.04, I wanted to add information to the statistics file as follows:

filegen rawstats file rawstats type day enable
filegen sysstats file sysstats type day enable

When I parse through the NTP log and restarting with the changed configuration, I see error messages indicating that the sysstats add rawstats could not be saved, permission denied.

I tried to create blank log files with touch and restarting ntp, though the errors persist.

The previous statistics log entries are working, so I am not sure what I missed that is causing this error.

---

