---
title: "Cron Job Not Working"
date: 2010-10-30
forum: General Help
---

### Post by RocketMain on 2010-10-30
After I create a cron job to shred some documents it seems to start and then immediately stop. What am I doing wrong? For instance, here is my cron:

#!/bin/sh
DISPLAY=:0.0
PATH = /usr/local/bin:/usr/bin:/usr/sbin:/bin:/sbin:


# m h  dom mon dow   command
17 18 * * * shred -uzv -n 20 /home/User/Downloads/D1/*
35 18 * * * shred -uzv -n 20 /home/User/Downloads/D2/*
50 18 * * * shred -uzv -n 20 /home/User/Downloads/D3/*

After I execute this I go into folder D1 and notice the first file has been slightly shredded, and then everything else is still the same as before.

Thanks for any help you give!!

---

### Post by DaithiF on 2010-10-31
Hi,
add 
```
MAILTO="" 

```

to the top of your crontab

see here [http://ubuntuforums.org/showthread.php?t=1537161](http://ubuntuforums.org/showthread.php?t=1537161) for more details

---

### Post by RocketMain on 2010-10-31
Works!

Dude, you ROCK!!!!

---

