---
title: "Will this script run?"
date: 2010-07-10
forum: General Help
---

### Post by redfox1160 on 2010-07-10
I have my cron set up like this:
```
0 1 * * 5 /usr/local/bin/tekzillaURL.sh ; /usr/local/bin/scamschoolURL.sh
5 1 * * 5 /usr/local/bin/tekzillaVID.sh ; /usr/local/bin/scamschoolVID.sh
10 1 * * 5 /usr/local/bin/tekzillaPER.sh ; /usr/local/bin/scamschoolPER.sh
```
Will these scripts run, or will I have to make different cron jobs for each script? Thanks.

---

### Post by DaithiF on 2010-07-11
Hi, yes you can put multiple commands onto a single line like this in cron and they should work.  But as per the other thread, you may want to combine the 3 scripts into one, and then have two cron entries, one for the tekzilla download, and another for the scamschool one.  I would then use separate cron entries for those two scripts since no particular reason to couple them into one.

---

