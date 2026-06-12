---
title: "run cron upon sign-in"
date: 2010-03-29
forum: General Help
---

### Post by LuniTux on 2010-03-29
Hello,

I am using Ubuntu 9.10 and was wondering if there was a way to start cron when a user signs in. i tried writing a manual script but that did not seem to work.

```

sudo service cron start

```

is there another way to do this?

---

### Post by cjhabs on 2010-03-29
> **LuniTux said:**
> Hello,

I am using Ubuntu 9.10 and was wondering if there was a way to start cron when a user signs in. i tried writing a manual script but that did not seem to work.

```

sudo service cron start

```

is there another way to do this?

You should not need to do this as it is always running.
from the man page
```

cron  is  started automatically from /etc/init.d on entering multi-user runlevels.


```

---

### Post by ciscosurfer on 2010-03-29
Not sure if you need this or not, but here is the community doc page: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

nixCraft cron page: [http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)

---

### Post by LuniTux on 2010-03-29
for some reason ubuntu removed everything from my crontab file. even the original comment telling you the settings... will this happen every time the computer restarts?

---

### Post by cjhabs on 2010-03-29
> **LuniTux said:**
> for some reason ubuntu removed everything from my crontab file. even the original comment telling you the settings... will this happen every time the computer restarts?

It should never happen. The only related thing I have seen is if you add an entry with incorrect syntax, it will not save it - but you can see that immediately by looking at the file.

Is this happening consistently?

I don't know how new you are to this. I would try this:
Add an entry to do something every couple of minutes - make sure it is running as expected - then reboot and see if it is still running after the reboot.

---

