---
title: "Ubunu throws me out to login prompt after few minutes"
date: 2012-07-25
forum: General Help
---

### Post by niranjan_rao on 2012-07-25
I have clean installation of 12.04 on my fujitsu laptop and 11.* before that. Never faced this kind of problem I am facing for last 5-6 days.

Normally I don't shutdown the laptop, just clone the lid. When I start it again, I get the login prompt as expected. I login, see all my previous applications running again as expected. After few minutes, I am suddenly logged out of the system, thrown to the login prompt again.

When I login again, system says that there was a system error and if I want to log a bug. I tried logging a bug, but then it tells me development is no longer done on this version of release.

A quick look at log file does not reveal anything interesting, but then I am not expert and might have missed entries from large log files.

I have couple of other ubuntu workstations available at home/work with same version and don't face this kind of problem on any of those machines.

Any help is greatly appreciated - its becoming very annoying as I keep loosing my work.

---

### Post by niranjan_rao on 2012-07-25
I found out in the log files colord[1474]: segfault at be ip b5fe0ed6 sp b545afb0 error 4 in libdbus-1.so.3.5.8[b5fb6000+47000]. There seems to be bug logged for this, but no resoultion. Any one has any ideas, please share

---

