---
title: "HUGE syslog and daemon.log files"
date: 2010-07-25
forum: General Help
---

### Post by kliffs on 2010-07-25
I have a 60GB partition with / and home on it. I logged on yesterday and it gave me a warning saying that I had only 1.9 GB of disk space left. I ignored it for a day and assumed that i had too many videos and pics. But the next day i had not added any files or downloaded any software but i had 0B left. I used the disk usage analyser and found that 33GBs came from /var/log. It was from two log files. syslog and daemon.log 16.5GB each!! I opened them up and i found that this line of text was repeated hnundreds of thousands of times.

```
Jul 22 19:32:36 aulenback-desktop ntfs-3g[5315]: Failed to decompress file: Value too large for defined data type
Jul 22 !9:32:36 aulenback-desktop ntfs-3g[5315]: ntfs_attr_pread error reading '/documents and setting/aulenback/My Documents?My Pictures/2007_01_13/_MG_0770.CR2' at offset 724002: 4096 <> -1: Value too large for defined data type
```

It seems to be reffering to My Pictures on the XP partition of the computer. What can i do to stop this and in the mean time is it safe to delete syslog and daemon.log?

---

### Post by AlphaLexman on 2010-07-25
Unix / Linux /ubuntu keeps LOTS of log files in '/var/log/' you can use the program 'logrotate' to manage your log files. Without this log rotation, every harddisk will fill up eventually.

---

### Post by jetole on 2010-11-14
Alphaman is right however logrotate is already setup on every Ubuntu install at least from Dapper (6.06 / June 2006) through to the current release (10.10 at the time of writing) and it knows how to handle syslog, daemon.log and many many more.

if you want to force a log rotation, you can run the command ***/usr/sbin/logrotate -f /etc/logrotate.d/rsyslog*** and it will rotate the log. If you want to delete the massive file (since by default, on Ubuntu, logrotate needs 7 days before it deletes syslog and syslog related file which includes daemon.log) then run ***rm -v /var/log/syslog /var/log/daemon.log && /usr/sbin/logrotate -f /etc/logrotate.d/rsyslog***. This will make sure the new file is properly created so that the daemons which log to it can continue to run.

The thing that has perked my interest about this is that logrotate and the way it is setup by default on Ubuntu will rotate these logs daily and delete the logs once they are older then 7 days. This means on day 1, syslog is renamed to syslog.1. on day 7 syslog.6.gz is renamed to syslog.7.gz. on Day 8, syslog.7.gz is deleted and the what was syslog.6.gz is now the new syslog.7.gz.

So assuming you haven't changed the logrotate configuration files (/etc/logrotate.conf and all files in /etc/logrotate.d) and assuming you haven't disabled logrotate from running (you can double check by looking for the file ls /etc/cron.daily/logrotate) then I would be more concerned with how many of these alerts you are getting and how often. A log should always fill with data and with syslog especially it _WILL_ always fill with data but 16.5 GB in one day is _WAY_ more then any system should ever expect (with possible exceptions in some specialty type of custom server setups etc).

If this is still occuring and, if these errors are identical as you have mentioned, you can run the command ***export checkLog="/var/log/syslog" && grep -m 1 'aulenback-desktop ntfs-3g' "${checkLog}" && grep 'aulenback-desktop ntfs-3g' "${checkLog}" | tail -1 && grep 'aulenback-desktop ntfs-3g' | wc -l && unset checkLog***. This will show you the time of the first entry since the log has been rotated, the time of the latest entry and the count of how many occurrences there have been in the log since it was rotated. If this number is really as high 16.5 GB in one day then something is definitely wrong and you will really want to investigate this.

**Hope this helps.**

---

### Post by kliffs on 2010-11-14
Hi,
Thanks for your help,
Yes i am aware of logrotate and how to use it but the problem didn't lie in logrotate. I was copying my pictures over a network share to my laptop. This took a long time because i had many GB of them. There was an error with a .cr2 image that it kept reporting over and over again until i deleted that particular image off the computer. I dont understand why it reported this so many times but after i manually removed the two logs everything went back to normal. I have no idea how it could have racked up 16 Gigs in one day but i think this is an isolated incident with my computer so...

---

