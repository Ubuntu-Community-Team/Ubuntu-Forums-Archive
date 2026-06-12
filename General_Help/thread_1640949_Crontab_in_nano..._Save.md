---
title: "Crontab in nano... Save?"
date: 2010-12-08
forum: General Help
---

### Post by th1bill on 2010-12-08
I have placed changer in my home directory (Ubuntu 10.04) and it is proported to change my desktop wallpaper.  According to the documentation I found this cron script shown below will trigger Changer every 2 minutes, my problem is I have invoked nano with the command "crontab -e" and have entered the script but I cannot find documentation on how to save.

Any help will be appreciated.

> */2 * * * *  /home/willis/changer

---

### Post by sisco311 on 2010-12-08
Ctrl+x, y, Enter.

Ctrl+g for help.

---

### Post by th1bill on 2010-12-08
> **sisco311 said:**
> Ctrl+x, y, Enter.

Ctrl+g for help.

thanks a lot, that saved it... Now I'll work on why I can run changer manually and it rotates the background one time, just as it is supposed to but the script does not seem to do that.

---

