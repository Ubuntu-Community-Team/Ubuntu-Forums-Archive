---
title: "Cron in hoary?"
date: 2005-03-15
forum: General Help
---

### Post by Biffy on 2005-03-15
I am using hoary and i have noticed that sometimes, my HDD starts working and slows my system down. After some research, i have come to the conclusion that it is cron that is being started.

I have used a lot of distros before, but i have no experience of cron whatsover. Why is there a cronjob? What exactly is it doing? Does this happen to all Ubuntu users?

---

### Post by alastair on 2005-03-15
See : 

man cron
man 5 crontab
man anacron
etc.

It just periodically schedules a command to run e.g. to rotate log files, index disk files (man slocate/updatedb), flush mail logs etc.

---

### Post by Biffy on 2005-03-15
[QUOTE=alastair]See : 

man cron
man 5 crontab
man anacron
etc.

It just periodically schedules a command to run e.g. to rotate log files, index disk files (man slocate/updatedb), flush mail logs etc.[/QUOTE]

Oh, ok. It's good for the system! I was just curious.

---

