---
title: "Logrotate - Duplicate Entry error"
date: 2009-11-16
forum: General Help
---

### Post by SiHa on 2009-11-16
Hi,

Wonder if someone can help a newcomer (I usually lurk over in the Mythbuntu forum).

I'm trying to get get logrotate working with a single logfile (/var/log/mythtv/mythfrontend.log).

The entry in /etc/logrotate.d/logrotate.conf is:```
/var/log/mythtv/*.log {
missingok
daily
create 0660 frontend mythtv
rotate 5
}

```

But if I manually run logrotate, I get the following:```
error: mythfrontend:33 duplicate log entry for /var/log/mythtv/mythfrontend.log
/var/log/mythtv/mythfrontend.log had errors, skipping.

```

Synax might be slightly out, it's from memory.

Running with the '-d' option produces no more information, simply the same two lines at the end of the output. No 'Considering Mythfrontend.log' or anything like that.
Running with '-df' does give me a line that says something like 'Forcing rotation of mythfrontend.log', but it doesn't actually do anything.

The contents of the /var/log/mythtv are: jamu.log, mythfrontend.log and mtd.log.

If I comment out all options, so it will use the defaults:
```
/var/log/mythtv/*.log {
#missingok
#daily
#create 0660 frontend mythtv
#rotate 5
}

```I get exactly the same results.

I'm stumped now, and would welcome any suggestions.

Thanks.

Simon

EDIT: Looks like it was user error. The Mythtv-frontend entry was already int /etc/logrotate.d. The 'problem' was that it had a filesize of 10M set, meaning it would not rotate until it the file got to that size. I wanted it to rotate daily, as in previous versions, so I removed this line.

---

