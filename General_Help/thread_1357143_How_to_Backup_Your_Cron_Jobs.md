---
title: "How to Backup Your Cron Jobs"
date: 2009-12-16
forum: General Help
---

### Post by Cerin on 2009-12-16
How do you backup/restore all your custom cron jobs? I'm not even sure where they're stored. I looked in /etc/crontab, but that just lists parts organized in /etc/cron.hourly/daily/weekly/etc, and none of those contained by jobs either.

---

### Post by john newbuntu on 2009-12-16
I think it goes into /var/spool/cron/crontabs/

---

### Post by Chesamo on 2009-12-16
If you want, you can do a normal [FONT="Courier New"]crontab -e[/FONT], then save the file somewhere else.

EDIT: Or better yet, just:
```
crontab -l > ~/Desktop/cron.txt
```
This will spit out a copy of your cron enteries into a file called "cron.txt" on your Desktop.

As for restoring them... I'm not entirely sure. You could open the file in gedit ("Text Editor") then copy/paste into the [FONT="Courier New"]crontab[/FONT] session. [FONT="Courier New"]gnome-terminal[/FONT] supports pasting into [FONT="Courier New"]nano[/FONT].

---

### Post by Cerin on 2009-12-16
Yep, my jobs appear to be in /var/spool/cron/username. Thanks guys.

---

