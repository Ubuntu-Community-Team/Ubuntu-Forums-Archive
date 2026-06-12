---
title: "MythTV database gone screwy"
date: 2009-11-06
forum: General Help
---

### Post by whein on 2009-11-06
I noticed a little while back that my MythTv setup was starting to screw things up.  My hardware setup is a primary and a secondary backend, with a pchdtv-5500 tuner on the primary and two Hauppauge PVR-150s and a PVR-350 on the secondary.  The secondary still seems to be working just fine with all tuners.  The primary backend was working fine until a few weeks ago.  Then the primary backend would record the right show, but the descriptive blurb in the "Watch Recordings" screen would be for a totally different show.  The descriptions in the "Schedule Recordings" screen seemed to be ok.  Then I noticed that starting on November 1st, every recording on the pchdtv-5500 wound up recording the at the wrong time.  So instead of Family Guy I would get Seinfield (shudder).  Or for many of them it can't find the recording file at all!  Now, mind you the secondary backend with all three tuner cards is still working just fine.

Searching the backend logs, I noticed a lot of entries like:
```
2009-11-04 03:53:12.648 DB Error (change_program):
Query was:
UPDATE program SET starttime = '2009-11-06T00:00:00',     endtime   = '2009-11-06T00:37:00' WHERE chanid    = 1111 AND       starttime = '2009-11-05T23:35:00'
Driver error was [2/1062]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate entry '1111-2009-11-06 00:00:00-0' for key 1

```

I've already guessed (and Google searching seems to confirm) that this is a database error, but I've found little help in solving the problem, and what recommendations I did find went WAY over my head.  Can someone help me fix this?  I can follow command line instructions well if spelled out, but advice like "dump the mysql tables and repair" needs a lot more detail.  I understand the theory of MySQL databases but have barely more than zero experience with them and my code-foo is weak.

Any takers?

-Will

---

