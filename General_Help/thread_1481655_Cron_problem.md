---
title: "Cron problem"
date: 2010-05-12
forum: General Help
---

### Post by Cavs23 on 2010-05-12
On ubuntu 9.10 I forgot to backup my cron folder. So I forgot how I got my php script in cron to work.

Right now it is 

```

0 0 * * * root lynx --dump /var/www/file.php > /dev/null

```

in sudo crontab -e

The file opens an http connection to a website several times and receives user data and dumps it to a file. I just don't remember how I had it set up. Or does it just go into crontab -e without sudo?

---

### Post by LoneWolfJack on 2010-05-13
when using sudo, you will edit the root user's crontab (most of the time not a good idea).

other than that, you don't need to open a php script in lynx to have it executed. try something like this:
```
0 0 * * * php /var/www/file.php > /dev/null
```

---

### Post by Cavs23 on 2010-05-14
That didn't work either. If it helps at all, I can't even find the cron log folders.

---

### Post by Cavs23 on 2010-05-15
up

---

