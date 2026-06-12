---
title: "Cron hourly with daily log file"
date: 2012-05-11
forum: General Help
---

### Post by amhainen on 2012-05-11
I have a cron task that I'm running every hour. I'd like to save the output to a log file by day.

```
0 * * * * /home/user/do.sh >> /home/user/logs/[date +%Y%m%d].log
```

I know that the part in the [date +%Y%m%d].log isn't valid. My low tech solution is to produce hourly logs and then have another daily cron to cat all the hourly logs and delete.

How can I pass some output (e.g. 'date +%Y%m%d') to use in a file name? So like today, I'd have:

```
(date +%Y%m%d).log = 20120511.log
```

---

### Post by amhainen on 2012-05-11
I found [this thread]("http://ubuntuforums.org/showthread.php?p=8865599") as a close item.

> 
```
shellvar=$(date +%d)
```
should give you today's day of the month in the variable shellvar.

So it looks like I need to use a shell variable?

---

### Post by cmont899 on 2012-05-11
You can add backtics (top left corner of the keyboard, under the ESC key) to run the command inline:

0 * * * * /home/user/do.sh >> /home/user/logs/`date +%Y%m%d`.log

---

### Post by amhainen on 2012-05-11
Great! That worked...thanks so much!

---

