---
title: "cronjob does not work!!!"
date: 2011-07-02
forum: General Help
---

### Post by Dlinux123 on 2011-07-02
I am attempting to create crontab file (user specific) for starters i am just trying to get one up and going. 
I used  <crontab -e> to enter the editor for my crontab once in there i enter:

<* * * * * /usr/bin/xterm>

what am I missing because it won't execute, if im understanding this right with all  '*' the cron should execute every minute.

---

### Post by prodigy_ on 2011-07-02
Try:
```
* * * * * DISPLAY=:0.0 /usr/bin/xterm
```

---

