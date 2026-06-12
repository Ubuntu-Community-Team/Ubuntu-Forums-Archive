---
title: "Getting cron/php to run"
date: 2010-08-01
forum: General Help
---

### Post by dgildeh on 2010-08-01
Hi everyone,

I've been struggling with this one for a while now so wanted to reach out to the community for help. Basically I created a php script for our server that executes every hour as a cron job. The full script and details are provided here:

[http://www.sambastream.com/blogs/dgildeh/12-03-10/implementing-revolving-backups-aws-ec2](http://www.sambastream.com/blogs/dgildeh/12-03-10/implementing-revolving-backups-aws-ec2)

The specific php script is remove_old_snapshots.php.

For some reason the php script doesn't execute to remove old snapshots. It works if I manually run it but not through a cronjob. I've added:

#!/usr/bin/php -q

To the top of the file and also modified the cron expression to:

```
*/1 * * * * /usr/bin/php -f /opt/Scripts/backup/remove_old_snapshots.php -v vol-XXXXXXX -n 400
```For testing. Still nothing appears to work to get this to run.

I'm using the php-cli libraries. php -v outputs:

PHP 5.2.6-3ubuntu4.5 with Suhosin-Patch 0.9.6.2 (cli) (built: Jan  6 2010 22:25:33)
Copyright (c) 1997-2008 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2008 Zend Technologies

My PHP is not installed as CGI but as an Apache module, but not sure if this affects php-cli program.

Any help as to why the php doesn't run during cron would be extremely appreciated as I've been struggling with this for weeks now!

Thanks

---

### Post by DaithiF on 2010-08-02
Hi,
2 things:
1. does this server have a MTA (mail transfer agent) installed?  If not, put MAILTO="" at the top of your crontab file
(see [http://ubuntuforums.org/showpost.php?p=7954400&postcount=6](http://ubuntuforums.org/showpost.php?p=7954400&postcount=6)) for explanation
2. if that isn't the problem, then capture the output from the php job in a log file to see what error messages may be generated:
```
*/1 * * * * /usr/bin/php -f /opt/Scripts/backup/remove_old_snapshots.php -v vol-XXXXXXX -n 400 **&> /some/path/to/logfile**
```

---

### Post by dgildeh on 2010-08-02
Thanks DaithiF for a prod in the right direction. As soon as I wrote the output of the job to a log file I could see the problem (not sure why I never tried that before!). I wasn't escaping the arguments so my -v for volume argument was causing the php client to just show the version and not execute the script. The correct statement is:

```
*/1 * * * * /usr/bin/php -f /opt/Scripts/backup/remove_old_snapshots.php **-- args** -v vol-XXXXXXX -n 400
```

Very relieved! Thanks

---

