---
title: "&quot;Simple Backup&quot; has stopped backing up!"
date: 2006-05-10
forum: General Help
---

### Post by katiad on 2006-05-10
Got an issue here. I've been using Simple Backup to backup my files on a daily basis - a full backup every 7 days, plus incremental backups every day, which I burn to cd. I've scheduled it for noon every day, when I'm not using the computer. It worked great at first, but now... it doesn't back anything up unless I do a forced manual backup. I've checked the settings - it's still set for noon. I've checked the system logs, and cron seems to start the daemon... but no backup is made.

Checked my local mail, and I get this message every day: "E: Another Simple Backup daemon already running: exiting"

I am at a loss of how to fix this. Help, please! :confused:

---

### Post by katiad on 2006-05-12
*bump* One last effort...

---

### Post by petit_prince on 2007-01-08
I had the same symptoms. Browsing the web I found out that sbackup apparently creates a lock file in /root called sbackup.lock in order to keep the program from starting if it's already running. Now guess what happens if this file happens to NOT get deleted? Exactly... sbackup claims it's already running.

Hope this solves your problem. Please let me know.

Credits go to
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2006-07/msg03143.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2006-07/msg03143.html)

---

