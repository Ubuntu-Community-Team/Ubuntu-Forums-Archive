---
title: "Quick cron question"
date: 2012-06-16
forum: General Help
---

### Post by grizzly on 2012-06-16
hi	
would this cron entry run every monday, wednesday , friday at 3AM ? 
> 0 3 * * 1,3,5 php /var/www/path-to-script.php

and will the following run everyday at 7 and 12 AM everyday ?
> 0 7,12 * * * php /var/www/

Just confirming ..

ty

---

### Post by Cheesemill on 2012-06-16
Looks good to me.
You may have to use the full path to php though.

---

### Post by grizzly on 2012-06-16
Thanks cheesmill

---

### Post by codemaniac on 2012-06-16
I use the below comments in every crontab .

> # minute (0-59),
# |      hour (0-23),
# |      |       day of the month (1-31),
# |      |       |       month of the year (1-12),
# |      |       |       |       day of the week (0-6 with 0=Sunday).
# |      |       |       |       |       commands

---

### Post by Cheesemill on 2012-06-16
> **codemaniac said:**
> I use the below comments in every crontab .
Good tip, I've added it to all of my crontabs.

---

