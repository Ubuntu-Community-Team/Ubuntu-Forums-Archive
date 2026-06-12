---
title: "What's the use of &quot;(double quotes) in Shell Scripting"
date: 2012-09-14
forum: General Help
---

### Post by Mohan1289 on 2012-09-14
Hi guys What's the use of " "(double quotes) in Shell Scripting

where can we use them... are there any syntaxes??

---

### Post by sisco311 on 2012-09-14
Please check out:
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by Lars Noodén on 2012-09-14
In a nutshell, the double quotes  are interpreted and the single quotes are literal.

```

$ test="Hello, World"
$ echo "I said, $test"
I said, Hello, World
$ echo 'I said, $test'
I said, $test


```

---

### Post by Mohan1289 on 2012-09-14
i want to create a backup file everyday using shellscript

when i googled for that ubuntu forum showed like this..
backup_files="/home /var/spool/mail /etc /root /boot /opt"can any one explain me this are we storing the data of all those directories in backup_files or it's just a name we used instead of using all those directory paths??

---

### Post by Lars Noodén on 2012-09-14
For backups, one of the first choices is [rsync](http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html)
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

The options -a -v and -H might be of most relevance.

Once you have your script figured out, you can launch it using [cron](http://manpages.ubuntu.com/manpages/precise/en/man1/crontab.1posix.html)

---

### Post by Mohan1289 on 2012-09-14
what's the use of cron?? Does it restores data from Backup files??

---

### Post by Lars Noodén on 2012-09-14
The link in #5 above gives the technical details for cron, but it allows you to schedule scripts to run at regular, defined intervals.  The interval can be once every hour, day, week or month or at specific times in between.

See also:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

