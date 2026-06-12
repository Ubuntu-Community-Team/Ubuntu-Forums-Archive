---
title: "Gnome scheduled tasks"
date: 2012-03-29
forum: General Help
---

### Post by jmumby on 2012-03-29
Need to run a cron job every minute. used the GUI 'Scheduled tasks' when I run the job from 'Scheduled tasks' it does as i expect. Blindly expected it to start running the cron every minute but does nothing. I assume there is something 'else' command line like that needs to be turned on. Any clues?

---

### Post by Habitual on 2012-03-30
post the cron entry please.

terminal > 
```
crontab -l
``` (That's an El, not capital i)

---

### Post by Azdour on 2012-03-30
Hi,

The thing that usually catches me out is that when it runs under cron you need to use full paths to any commands.

---

