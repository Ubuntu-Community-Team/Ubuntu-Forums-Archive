---
title: "Where is crontab stored?"
date: 2010-12-12
forum: General Help
---

### Post by seangee on 2010-12-12
Hi all

Just had to replace by boot disk which is on a USB stick. Fortunately I had a backup that isn't too far out of date. I have recently created some root cron tasks by running crontab -e.

I can still read the corrubt usb stick - but where do I fund the cron entries?

---

### Post by AlphaLexman on 2010-12-12
They should be in the directories:
[LIST]
[*]/etc/cron.d/
[*]/etc/cron.daily/
[*]/etc/cron.hourly/
[*]/etc/cron.monthly/
[*]/etc/cron.weekly/
[/LIST]

---

### Post by Cheesehead on 2010-12-12
Root-level crontab should be in /etc/crontab.
Root-level anacron and periodics should be in /etc/cron*

User-level crontabs should be in /var/spool/cron/crontabs
Note that even though they are user level, sudo access is required to view them there. Users should view(copy) their crontab using 'crontab -l'. Also, copying a fresh crontab into /var/spool/cron/crontabs is a very bad idea. Users should use 'crontab -e' and paste their old crontab contents in.

For users, the 'crontab' command does a couple handy things: It checks syntax, and it also tells cron to reload the crontab once written. So the whole system is set up to really force users to use the command instead of copying and pasting and wondering why things broke.

---

### Post by seangee on 2010-12-13
Ta - that's what I was after. Quite happy to use crontab -e to set it up. I just want to make sure I haven't missed anything that is in there, and have all the correct params.

Will check it out tonight.

---

### Post by P1C0 on 2010-12-13
> **seangee said:**
> Ta - that's what I was after. Quite happy to use crontab -e to set it up. I just want to make sure I haven't missed anything that is in there, and have all the correct params.

Will check it out tonight.Just make sure u use 'export DISPLAY=:0' if u want to start a gui application.

---

### Post by seangee on 2010-12-13
All sorted :D

---

