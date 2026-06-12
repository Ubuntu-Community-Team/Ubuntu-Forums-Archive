---
title: "Run a script on day's first login?"
date: 2010-04-06
forum: General Help
---

### Post by karmic-koala on 2010-04-06
Is there a way to schedule a script to be run on day's first login by a certain user /any user?

Crontab will execute a script at fixed times and will fail if the computer is not switched on. Is there a way to trigger a script on a user's login then? 

PS script should only run once a day, no more.

---

### Post by cjhabs on 2010-04-06
> **karmic-koala said:**
> Is there a way to schedule a script to be run on day's first login by a certain user /any user?

Crontab will execute a script at fixed times and will fail if the computer is not switched on. Is there a way to trigger a script on a user's login then? 

PS script should only run once a day, no more.

I don't know of an elegant way, but you could modify the script to create a log file with a date stamp and only execute the rest of the script if that date stamp does not match today's date.

---

### Post by karmic-koala on 2010-04-06
> **cjhabs said:**
> I don't know of an elegant way, but you could modify the script to create a log file with a date stamp and only execute the rest of the script if that date stamp does not match today's date.

Thats a clever way to do it :)

Do you think that will add much load or add to start up time, checking the log file I mean. I could probably schedule it @reboot in crontab.

---

### Post by new_tolinux on 2010-04-06
> **karmic-koala said:**
> Thats a clever way to do it :)

Do you think that will add much load or add to start up time, checking the log file I mean. I could probably schedule it @reboot in crontab.
That depends on how you log it and on the script.

Have a logfile of several gigabytes, and it will add.
Have a 10minute 100%cpu-time script and it will add.

But generally..... it shouldn't be noticed, only take a few miliseconds.

---

### Post by cjhabs on 2010-04-06
My suggestion is to write a one line log file that you overwrite each time, so all it contains is the date stamp - then there will be no noticeable overhead (so long as you place the log file on a local filesystem). I would recommend making it a dot file in the user's home folder - or subfolder.

---

### Post by cjhabs on 2010-04-06
Or - you could even make the log file empty and simply "touch" it after checking it's timestamp.

---

### Post by lavinog on 2010-04-06
> **karmic-koala said:**
> Is there a way to schedule a script to be run on day's first login by a certain user /any user?

Crontab will execute a script at fixed times and will fail if the computer is not switched on. Is there a way to trigger a script on a user's login then? 

PS script should only run once a day, no more.

What kind of permissions does the script need?  If the script needs elevated privileges then running it in user space will cause problems.

Utilize cron with the touched file idea.
have cron run your script every 30 mins.

Your script should check the existance of a run file and the datestamp.
You could use /var/run for the location of the file (it uses ram instead of hard drive, so it will respond quicker)

if the file doesn't exist or the datestamp is not today, run the script and use touch to create the file.
if the file exists and the datestamp is todays date, the script should end.  This should have no impact on performance.

---

### Post by dcstar on 2010-04-06
> **karmic-koala said:**
> Is there a way to schedule a script to be run on day's first login by a certain user /any user?

Crontab will execute a script at fixed times and will fail if the computer is not switched on. Is there a way to trigger a script on a user's login then? 

PS script should only run once a day, no more.

Items in the cron.daily folder will be executed once per day after the machine is booted - that is exactly what anacron is for.

---

### Post by lavinog on 2010-04-06
> **dcstar said:**
> Items in the cron.daily folder will be executed once per day after the machine is booted - that is exactly what anacron is for.

Of course
:-)

---

### Post by cjhabs on 2010-04-07
That is good to know - I wasn't aware of that.

---

### Post by karmic-koala on 2010-04-09
> **dcstar said:**
> Items in the cron.daily folder will be executed once per day after the machine is booted - that is exactly what anacron is for.

I didn't now that either! Good to know.

---

