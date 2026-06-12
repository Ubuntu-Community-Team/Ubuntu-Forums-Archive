---
title: "Cron/Fetchmail locked up system"
date: 2009-08-22
forum: General Help
---

### Post by ricster on 2009-08-22
I have fetchmail set to run every 5 mins and it usually runs fine for a week or two but sometimes the system just hangs, after rummaging through the logfiles i found this as the last entry in syslog before i rebooted it at 8:30 this morning. Fetchmail runs fine at 4:30 and pulls down an email (which is a well formed, i checked it) and passes it to my mailbox through potfix. All is good. It then starts up again 5 mins later and four mins after that the final log entry is posted. any ideas anyone?


```
Aug 22 04:30:01 localhost /USR/SBIN/CRON[28837]: (root) CMD (/etc/webmin/fetchmail/check.pl --null)
Aug 22 04:30:02 localhost postfix/smtpd[28841]: connect from localhost[127.0.0.1]
Aug 22 04:30:02 localhost postfix/smtpd[28841]: 8FA1AF2AF5: client=localhost[127.0.0.1]
Aug 22 04:30:02 localhost postfix/cleanup[28844]: 8FA1AF2AF5: message-id=<########>
Aug 22 04:30:02 localhost postfix/qmgr[28206]: 8FA1AF2AF5: from=<[################, size=9342, nrcpt=1 (queue active)
Aug 22 04:30:02 localhost postfix/local[28845]: 8FA1AF2AF5: to=<ric@localhost>, relay=local, delay=0.12, delays=0.07/0.02/0/0.02, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Aug 22 04:30:02 localhost postfix/qmgr[28206]: 8FA1AF2AF5: removed
Aug 22 04:30:02 localhost postfix/smtpd[28841]: disconnect from localhost[127.0.0.1]
Aug 22 04:35:01 localhost /USR/SBIN/CRON[28851]: (root) CMD (/etc/webmin/fetchmail/check.pl --null)
Aug 22 04:39:01 localhost /USR/SBIN/CRON[28859]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)

```

---

