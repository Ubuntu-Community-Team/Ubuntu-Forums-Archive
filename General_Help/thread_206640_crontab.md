---
title: "crontab"
date: 2006-06-30
forum: General Help
---

### Post by metallcoholix on 2006-06-30
Hi, im programming a task in the crontab -e, what I wrote is
* * * * * sudo mv /home/user/Desktop/doc1.txt /home/user/Docs
this file is intended to move every minute to /home/user/Docs, however my crontab doesnt seems to be working, though it worked fine two days ago, any ideas??
Thx

---

### Post by mbeierl on 2006-06-30
If you want the crontab to run as root, you should edit root's crontab:

[FONT="Courier New"]sudo crontab -e[/FONT]

and put the entry in there.  I'm not sure that the sudo inside the crontab entry will work as it should be prompting you for your password.  It may have worked originally as sudo does cache the password temporarily - although I'm not sure that it would for the cron daemon.

---

