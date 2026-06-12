---
title: "Gnome-Schedule 2.1.1; Cron jobs"
date: 2010-07-18
forum: General Help
---

### Post by strange_cathect on 2010-07-18
I've been trying to get gnome-schedule to perform an automatic backup for me using grsync. However, gnome-schedule will not initiate any scheduled commands.

First, I wrote a script and tried to have gnome-schedule run it. I named a file "backup.sh" and told gnome-schedule where to find it. The script reads:

> #!/bin/sh
grsync -e "Internal Backup";
touch test file location;


I can run the script in the terminal fine, but gnome-schedule won't seem to initiate it at the requested time.

After this failed I dispensed with the script file and just created a new task command that reads:

> 
grsync -e "Internal Backup"

Again, I can ask gnome-schedule to run this task successfully by clicking "run task" but it will not run this as a scheduled event.

What is up with that?

---

