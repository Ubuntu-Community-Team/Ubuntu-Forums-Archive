---
title: "sendmail problem causes home directory to disappear"
date: 2011-07-15
forum: General Help
---

### Post by duffrecords on 2011-07-15
I wrote a script that is run by cron every 5 minutes, but for some weird reason it causes my home directory to disappear for any currenly logged-in sessions.  If I SSH in after that, my home directory will be present but once the cron job runs it will disappear again.  This is the script:
```
if [[ `ps aux | grep '[m]otion.pid'` = "" && ! -e /tmp/ignore-motion ]]; then
  echo "security cameras offline" | mail -s "" xxxxxxxxxx@xxxxx.com
fi
```
And there are a lot of these errors in /var/log/syslog:
```
Jul 14 07:51:01 burbank sendmail[16241]: p6EEp1I5016241: from=ian, size=397, class=0, nrcpts=1, msgid=<201107141451.p6EEp1I5016241@burbank>, relay=ian@localhost
Jul 14 07:51:01 burbank sendmail[16251]: My unqualified host name (burbank) unknown; sleeping for retry
Jul 14 07:51:01 burbank sendmail[16241]: p6EEp1I5016241: to=ian, ctladdr=ian (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30397, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Jul 14 07:52:01 burbank sendmail[16251]: unable to qualify my own domain name (burbank) -- using short name
Jul 14 07:52:01 burbank sendmail[16251]: p6EEq1Pq016251: from=ian, size=397, class=0, nrcpts=1, msgid=<201107141452.p6EEq1Pq016251@burbank>, relay=ian@localhost
Jul 14 07:52:01 burbank sendmail[16251]: p6EEq1Pq016251: to=ian, ctladdr=ian (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30397, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
```
I understand that sendmail is having trouble because of my hostname, but why would it cause my home directory to disappear?

---

### Post by duffrecords on 2011-08-01
Seems like it's related to cron, rather than sendmail.  I removed that cron job, which made the problem stop happening for a couple of weeks.  Yesterday I added a new cron job that runs every five minutes (but has nothing to do with sendmail) and my home directory started disappearing again.  It should be noted I encrypted my home directory and I think that has something to do with it.  Also, around the same time, SSH public key authentication stopped working, which also points to the encryption issue.

---

