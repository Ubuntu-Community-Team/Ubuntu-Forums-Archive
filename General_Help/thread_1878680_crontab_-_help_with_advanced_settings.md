---
title: "crontab - help with advanced settings"
date: 2011-11-10
forum: General Help
---

### Post by chrismyers on 2011-11-10
Hi Guys,
 
I am having trouble finding the correct syntax to create a cronjob that will run every 6 weeks (or 8 times a year). Even better if this will run on a Monday, but not essential.
 
I can't quite work this one out. It would be nice if @yearly/8 worked, but it doesn't.
 
Any help would be greatly appreciated.

---

### Post by mikewhatever on 2011-11-10
I am not a cron expert, but it seems that this particular task would be easier to accomplish with 8 separate cron jobs.

---

### Post by chrismyers on 2011-11-10
I was hoping you wouldn't say that.. I have about 30 jobs to create on a 6 week rota..
 
That would mean 240 cron jobs!
 
Any other suggstions anyone?

---

### Post by CharlesA on 2011-11-10
I don't think there is any way to have it run every 6 weeks. You can do it monthly, but if you wanted to do it every 6 weeks, I don't think that's possible.

Well unless you wanted to hack it with a script that sleeps for 2 weeks.. but that may cause more problems then not. Set cron to run a script in 4 weeks, and have a command to let the script sleep for 2 weeks. Nasty hack but it might be better then setting 30 + cronjobs a week.

Anyhow, if the jobs are predefined, you can just import them into cron at scheduled intervals, worth a shot I guess.

Anyhow, you can replace the current crontab with a file by running this:

```
crontab -u username somefile
```

See [here]("http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/") for some more infos.

---

### Post by matt_symes on 2011-11-10
Hi

Here's another idea. 

If this is a server that is not often rebooted then what about scheduling it using the *at* command.

The script you run could schedule another run for itself by calculating the date in 6 weeks time.

This could be abstracted into a script that calls your main worker script.

You could hook it into cron using the @reboot option. Rescheduling after a reboot could be handled by storing the date it needs to run in a file and using that to pass to the at command again.

I have not attempted this and i don't know if it's feasible so maybe someone like Charles could comment on it as i would not want to lead you up the proverbial garden path :)

Kind regards

---

### Post by CharlesA on 2011-11-10
> **matt_symes said:**
> Hi

Here's another idea. 

If this is a server that is not often rebooted then what about scheduling it using the *at* command.

The script you run could schedule another run for itself by calculating the date in 6 weeks time.

This could be abstracted into a script that calls your main worker script.

That's actually a good idea. I have used @reboot scripts before, but not in that matter.

My idea was to have a script wait 2 weeks and then run, but that might work too.

---

