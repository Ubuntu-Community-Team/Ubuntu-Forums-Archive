---
title: "Automatick folder space reducer"
date: 2011-02-19
forum: General Help
---

### Post by mike_info on 2011-02-19
Hi all,

I am at work right now, and my superiors asked me to write/find a shell script in linux that checks a folder size, and if the folder space size above the certain limit, it will automatically reduce the folder size.

Basically the folder contains only one log file e.g: main.log What I need your help is if the current folder disk space is increased to 80% means it will execute this command e.g: cp /dev/null main.log it will nullify the main.log to ZERO bit file.

also again it will check the current folder space. a automated mail should send the report like before disk space and after space.I need to cron this job daily.

Please help guys I need it very urgently!:(

Can anyone here help me find or help me create a script like that??

I thank you in advance,

Mike

---

### Post by Cheesehead on 2011-02-19
Take a look at **inotify**.
Tutorial at [http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html](http://www.ibm.com/developerworks/linux/library/l-ubuntu-inotify/index.html)

---

### Post by Dithers on 2011-02-22
you probably don't need to store Gobs of log data one day and none the next?... I would either use set it up to make a new file every so many days and delete old files... or remove lines based on date.

what if you need the log data 10 min after it clears?

---

