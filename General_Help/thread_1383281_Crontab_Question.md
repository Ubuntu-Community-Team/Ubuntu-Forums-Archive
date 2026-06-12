---
title: "Crontab Question"
date: 2010-01-17
forum: General Help
---

### Post by zappadragon on 2010-01-17
I want to run a script after the system has booted. I am trying to add the job to crontab but not sure how to write it. I want the script to just run once after boot so should it look like this?

1 * * * * /your/directory/myscript

I have never mess with cron until now and I don't want multipal occurances of the script runnnng.

Thanks

---

### Post by mobilediesel on 2010-01-17
> **zappadragon said:**
> I want to run a script after the system has booted. I am trying to add the job to crontab but not sure how to write it. I want the script to just run once after boot so should it look like this?

1 * * * * /your/directory/myscript

I have never mess with cron until now and I don't want multipal occurances of the script runnnng.

Thanks

No, do it like this:
```
@reboot /your/directory/myscript
```
That will run it one time only when you first boot.

Here's how the scheduling works:

* * * * * /path/to/command

field	 allowed values
-----	 --------------
minute	 0-59
hour		 0-23
day of month	 1-31
month	 1-12 (or names, see below)
day of week	 0-7 (0 or 7 is Sun, or use names)

@reboot	   Run once, at startup.
@yearly	   Run once a year, "0 0 1 1 *".
@annually	   (sames as @yearly)
@monthly	   Run once a month, "0 0 1 * *".
@weekly	   Run once a week, "0 0 * * 0".
@daily	   Run once a day, "0 0 * * *".
@midnight	   (same as @daily)
@hourly	   Run once an hour, "0 * * * *"

---

### Post by zappadragon on 2010-01-17
Hahaha thanks I was just getting ready to post the 

or I could just do 

@reboot /usr/local/bin/myscript

---

### Post by mobilediesel on 2010-01-17
> **zappadragon said:**
> Hahaha thanks I was just getting ready to post the 

or I could just do 

@reboot /usr/local/bin/myscript

I figured it'd be good to post more about cron's scheduling, too. I had a hell of a time searching for it the first time I messed with it.

---

### Post by zappadragon on 2010-01-17
Well I guess IPCOP does not understand @reboot :-(

---

### Post by mobilediesel on 2010-01-17
> **zappadragon said:**
> Well I guess IPCOP does not understand @reboot :-(

You could try this: [http://www.linuxquestions.org/questions/linux-networking-3/run-custom-script-at-boot-time-on-ipcop-651228/](http://www.linuxquestions.org/questions/linux-networking-3/run-custom-script-at-boot-time-on-ipcop-651228/)

---

