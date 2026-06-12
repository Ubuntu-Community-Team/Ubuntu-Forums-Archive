---
title: "INFO task updatedb.mlocat:8002 blocked"
date: 2012-10-10
forum: General Help
---

### Post by medha6 on 2012-10-10
When I was running MonetDB server and some queries on it overnight, with my LightDM was shut down, next morning I noticed following messages repeatedly appeared on my bash shell where I was running the MonetDB queries:
[B]
INFO task updatedb.mlocat:8002 blocked for more than 120 seconds
"echo 0" > /proc/sys/kernel/hung_task_timeout_secs disables this message[/B]

I am running Ubuntu 12.04 and uname -a gives:
[B]$ uname -a
Linux my-laptop 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux[/B]

I am a fairly seasoned user of Ubuntu and have been using it for past 4+ years. I don't think I had ever noticed this kind of message before on earlier versions or even on 12.04.

I googled for the error and saw quite a few links and even bug reports, but most of them are a couple of years old and none of the solutions seemed relevant to my problem.

Please help.

---

