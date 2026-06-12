---
title: "Can't suppress this cron output"
date: 2012-01-16
forum: General Help
---

### Post by deadtom on 2012-01-16
I have this cronjob set up:

```
[ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete
```I have no idea what it does, other than send me lots of messages. How do I suppress the messages it's sending?

I've tried adding /dev/null and /dev/null 2/&1 to the end of the command, this has worked to stop other cronjobs from sending messages but not this one.

Any ideas?

---

### Post by gsgleason on 2012-01-17
It deletes old files.

if /usr/lib/php5/maxlifetime is executable
and 
if /var/lib/php5 is a directory
then
find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete

It looks like it deletes any file inside /var/lib/php5/ that hasn't been modified in N minutes, where N is the output of /usr/lib/php5/maxlifetime

add this to the end to send all output to /dev/null: &>/dev/null

---

### Post by deadtom on 2012-01-17
> **gsgleason said:**
> add this to the end to send all output to /dev/null: &>/dev/null

I'll try that. Thanks!

---

