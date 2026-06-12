---
title: "Crontab and new line? Jobs stop working - editing crontab helps"
date: 2011-04-19
forum: General Help
---

### Post by smcap on 2011-04-19
Im having a very annoying issue with crontab on Ubuntu 10.04 (it does NOT exist on 8.04)...

Imagine the following scenario. At some point all my jobs are running. Then i, say, add a new line between job 1 and job 2. Both jobs stop executing ("status cron" shows start/running). I edit the cron and remove the new line between jobs 1 and 2. Jobs are still not executing. I crontab -e again, go to the last line, press Backspace and Delete keys, save. Jobs start executing. 

I can have a million empty lines at the end of a crontab but the same keeps happening whenever i modify the cron. I have to go to the last line, do some Backspace/Delete manipulations, and only then my jobs start running.

If that wasn't annoying enough, the whole thing breaks again after server reboot. It looks like ppl have been running into the same issue, and the article at [http://www.wellsphere.com/kidney-failure-article/cron-does-not-work-after-reboot-solved/639679](http://www.wellsphere.com/kidney-failure-article/cron-does-not-work-after-reboot-solved/639679) suggests the following:
[I]
Cron did not kick in after a reboot. For some reason, you had to edit the cron tab file after a server reboot for it to function. Many people had a similar problem and they simulate an edit for the cron to work after a reboot.
Beware - a simple "touch" does not work. You have to do a crontab -e, make some edit and then save it for this to work.[/I]

So we had to write a script to execute from another machine to check if the server in question was rebooted and then remotely edit its crontab by adding new line, saving, deleting new line, saving. This seems to be working, but seriously, is that what ppl have to go through to make sure cron jobs are executing on 10.04?!

---

### Post by smcap on 2011-04-21
bump

---

### Post by bleutyler on 2011-04-21
I've tried that tactic, and right now none of my crontab jobs are working.  not even a /bin/cp !

---

### Post by smcap on 2011-04-21
Then perhaps your issue is different from mine. I searched this forum before posting and noticed A LOT of various issues with crontab on different versions of Linux, but none seem to be the same as mine.

---

### Post by collisionystm on 2011-04-21
Perhaps its because your editing crontab while a job is executing?

Or maybe its the text editor you are using? 

Stay away from vi and use nano

vi has caused me so many issues with corruption.

---

### Post by smcap on 2011-04-25
Thanks for your ideas!

> **collisionystm said:**
> Perhaps its because your editing crontab while a job is executing?
Very possible! But how can i ensure that im editing crontab while no jobs are executing? Most of my jobs run every minute. (Please dont suggest killing whatever is running and modifying crontab fast :P)

> **collisionystm said:**
> 
Or maybe its the text editor you are using? 
Stay away from vi and use nano

I use Nano on the 10.04 machine that is giving me these issues. On 8.04 i have Jed.

---

### Post by smcap on 2011-04-25
> **smcap said:**
> I use Nano on the 10.04 machine that is giving me these issues. On 8.04 i have Jed.
I tested editing the crontab with Nano on 8.04 machine and did not run into the issues that i described here.

---

