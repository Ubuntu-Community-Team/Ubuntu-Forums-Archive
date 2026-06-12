---
title: "crontab not working"
date: 2009-07-02
forum: General Help
---

### Post by asadqamber on 2009-07-02
My cron deamon is running, I checked it with 

ps aux |grep cron

but no command is being executed, even  when the crontab had:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

*/2 * * * * echo "Print this every Two minutes"

any idea?

---

### Post by asadqamber on 2009-07-03
The output has to be redirected from 'echo' to a file if you want to see anything -- echo doesn't run in a particular terminal so you'd never see it otherwise. so this works

 	Code:
 	 * * * * * /bin/date >> /home/[your user]/test.out

---

