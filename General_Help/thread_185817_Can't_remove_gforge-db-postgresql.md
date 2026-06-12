---
title: "Can't remove gforge-db-postgresql"
date: 2006-06-01
forum: General Help
---

### Post by ChrisNTR on 2006-06-01
I installed gforge by mistake and now I can't remove it -

```
chrisntr@ubuntu6:/var/lib/dpkg/info$ sudo dpkg --purge gforge-db-postgresql
(Reading database ... 254260 files and directories currently installed.)
Removing gforge-db-postgresql ...
cp: cannot stat `/etc/postgresql/pg_hba.conf': No such file or directory
dpkg: error processing gforge-db-postgresql (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gforge-db-postgresql

```

---

### Post by jdralphs on 2006-06-06
Were you able to find a solution to this problem?  I'm having the same problem on breezy.

---

### Post by jdralphs on 2006-06-06
I haven't been able to find anyone else with a solution for this problem, so here's my makeshift one.  I'm kindof a newbie so ... it may or may not be a <i>good</i> solution.  (but, it does work.)

delete these files:
> etc/cron.d/gforge-db-postgresql
usr/lib/gforge/bin/calculate_user_metric.php
usr/lib/gforge/bin/check_stale_tracker_items.php
usr/lib/gforge/bin/db-upgrade.pl
usr/lib/gforge/bin/db_project_sums.php
usr/lib/gforge/bin/db_stats_agg.php
usr/lib/gforge/bin/db_trove_maint.php	
usr/lib/gforge/bin/install-db.sh
usr/lib/gforge/bin/massmail.php
usr/lib/gforge/bin/project_cleanup.php	
usr/lib/gforge/bin/project_weekly_metric.php
usr/lib/gforge/bin/rating_stats.php
usr/lib/gforge/bin/register-theme
usr/lib/gforge/bin/rotate_activity.php
usr/lib/gforge/bin/sf-add-skill
usr/lib/gforge/bin/site_stats.php
usr/lib/gforge/bin/stats_projects_logparse.pl
usr/lib/gforge/bin/unregister-theme
usr/lib/gforge/bin/vacuum.php
usr/lib/gforge/db/20021125.sql
usr/lib/gforge/db/20021212.sql
usr/lib/gforge/db/20021213.sql
usr/lib/gforge/db/20021214.sql
usr/lib/gforge/db/20021215.sql
usr/lib/gforge/db/20021216.sql
usr/lib/gforge/db/20021223-drops.sql
usr/lib/gforge/db/20021223.sql
usr/lib/gforge/db/20021230.sql
usr/lib/gforge/db/20030102-drops.sql
usr/lib/gforge/db/20030102.sql
usr/lib/gforge/db/20030105.sql
usr/lib/gforge/db/20030107.sql
usr/lib/gforge/db/20030109.sql
usr/lib/gforge/db/20030112.sql
usr/lib/gforge/db/20030113-drops.sql
usr/lib/gforge/db/20030113.sql
usr/lib/gforge/db/20030115.sql
usr/lib/gforge/db/20030131.sql
usr/lib/gforge/db/20030209.sql
usr/lib/gforge/db/20030312.sql
usr/lib/gforge/db/20030513.sql
usr/lib/gforge/db/20030822.sql
usr/lib/gforge/db/sf-2.6-complete.sql
usr/lib/gforge/db/sf2.5-to-sf2.6.sql	
usr/lib/gforge/db/view_bug.sql	
usr/lib/gforge/db/view_patch.sql
usr/lib/gforge/lib/sqlparser.pm
usr/share/doc/gforge-db-postgresql/README.Debian.gz
usr/share/doc/gforge-db-postgresql/changelog.Debian.gz
usr/share/doc/gforge-db-postgresql/changelog.gz
usr/share/doc/gforge-db-postgresql/copyright


make a backup of /var/lib/dpkg/status
```
cd /var/lib/dpkg/
cp status status.backup
```

open up /var/lib/dpkg/status with your favorite editor
```
nano status
```
and remove the entry for gforge-db-postgresql.
save the modified version an you are done.

'Best of luck

~Jason

---

### Post by yusufk on 2008-04-16
I've been frustrated MANY times with Gforge on Ubuntu. I can't believe that it still hasn't been fixed.

If it can't be fixed then please just remove the whole damn thing from the repos!

This is not the only package that wont remove, I've had problems with gforge-mta and others.

The simplest way to fix is to edit the dpkg scripts for the packages found at /var/lib/dpkg/info/ and comment out the "set -e" line.

Not sure what that does, but it works.

[http://ubuntuforums.org/images/smilies/icon_mad.gif](http://ubuntuforums.org/images/smilies/icon_mad.gif)
:mad:

---

