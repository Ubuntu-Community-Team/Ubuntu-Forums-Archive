---
title: "fcron"
date: 2011-09-10
forum: General Help
---

### Post by Robbyx on 2011-09-10
I have a simple bash script that I want to run daily. Looked at crons in synaptic and found fcron. It proposes to remove ubuntu-desktop. I stopped and asked here: will the removal mean that I will no longer have any graphical interface (I do not use unity)?

---

### Post by Toz on 2011-09-16
Why not just use the existing cron? If you're comfortable with the command line, ```
crontab -e
``` will open up a text-based editor that you can use to create a daily script. For example:
```
0 1 * * * /path/to/scipt
```
will run the script every day at 1am.

If you prefer a gui tool to schedule, have a look for **gnome-schedule** in the Software Centre.

---

