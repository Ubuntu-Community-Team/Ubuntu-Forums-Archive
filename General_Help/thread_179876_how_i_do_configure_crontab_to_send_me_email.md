---
title: "how i do configure cron/tab to send me email?"
date: 2006-05-20
forum: General Help
---

### Post by ice60 on 2006-05-20
hi, i've set up a couple of crontabs, which i'm sure shouldn't be sending me emails, i don't want them anyway. but, i'm sure i've seen a cron which is configurated to send daily emails and i'm certain it's either chkrootkit or perhaps rkhunter.

i think they would use MAILTO. does anyone use either of these rootkit checkers and have the MAILTO configured? can you point me in the right direction so i to can receive daily emails from my crons to?

thanks.

---

### Post by jpkotta on 2006-05-21
[QUOTE=cron manpage]
       cron  then  wakes up every minute, examining all stored crontabs, checking each command to see if it should be
       run in the current minute.  When executing commands, any output is mailed to the owner of the crontab  (or  to
       the  user  named  in  the MAILTO environment variable in the crontab, if such exists).  The children copies of
       cron running these processes have their name coerced to uppercase, as will be seen in the syslog and  ps  out&#8208;
       put.
[/QUOTE]

I think all you have to do is add a line like ```
MAILTO=ice60
``` I have not tried this.

---

