---
title: "Cron jobs running nine hours ahead of schedule"
date: 2012-02-02
forum: General Help
---

### Post by sohmc on 2012-02-02
I programmed the following cron job:
30 0 * * * /usr/bin/some_script.sh

The job executes fine but runs 9 hours ahead of schedule.  I thought this might be a timezone issue but my time is set correctly.  Besides, shouldn't cron run on LOCAL time and not on whatever timezone it's based on?

Is there something I should check to make sure that cron runs based on local time?

Thanks

---

### Post by hwttdz on 2012-02-02
That job runs at
00:30 every day.  

What indication do you have that the job is running at 09:30?

Do you have emails set-up for cron? 

What about making a 
* * * * * date > ~/current_time.txt
rule, and look at the contents of ~/current_time.txt, is the time in there correct?  Does it get updated every minute?

---

### Post by sudodus on 2012-02-02
How do you run cron: as your own user or as root?

(If you use crontab it is as your own user.)

---

### Post by sohmc on 2012-02-02
> **hwttdz said:**
> 
What indication do you have that the job is running at 09:30?

I get an e-mail at 1530 (3:30 pm) saying that the job was completed.  0930 would mean that it's running 9 hours LATE, not early, BTW.

> **hwttdz said:**
> 
What about making a 
* * * * * date > ~/current_time.txt
rule, and look at the contents of ~/current_time.txt, is the time in there correct?  Does it get updated every minute?

It shows the correct time.

> **sudodus said:**
> How do you run cron: as your own user or as root?

(If you use crontab it is as your own user.)

I use crontab.  I assume that it would run under my own user.

---

### Post by sudodus on 2012-02-02
I think it might actually start the right time. Maybe you can stay awake tonight, and check via the system monitor if a process starts running your script '/usr/bin/some_script.sh' at 0:30 (half past mid-night). Maybe your script runs longer than you think.

*Edit: You can also add a line in the beginning of your real script, that writes the current time (the same way as suggested by y hwttdz)*

---

### Post by sohmc on 2012-02-02
> **sudodus said:**
> I think it might actually start the right time. Maybe you can stay awake tonight, and check via the system monitor if a process starts running your script '/usr/bin/some_script.sh' at 0:30 (half past mid-night). Maybe your script runs longer than you think.

I can assure you that this is not the case.  If it were, it would show up on in my running processes.

The script takes milliseconds to complete.

Is it possible that cron is using a different timezone?

---

### Post by sohmc on 2012-02-02
It looks like the crontab file is providing some insight:

```

# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.

```

I'm looking for the cron daemon's settings...one would think it would be /etc/cron, but no dice.

---

### Post by sudodus on 2012-02-02
> **sohmc said:**
> It looks like the crontab file is providing some insight:

```

# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.

```

I'm looking for the cron daemon's settings...one would think it would be /etc/cron, but no dice.
I use a crontab script to have a talking clock tell the time every whole hour and half-hour. It is the same time as I see on the small applet (or with any clock program). So in that case you have another kind of locale setting.

---

### Post by sohmc on 2012-02-02
Even though I've restarted my machine several times since I set my timezone, I restarted the cron daemon separately to see if this makes a difference.  Guess I'll find out in a few hours.

---

### Post by sudodus on 2012-02-02
I'm sorry but I cannot really understand your problem. Maybe if you look at the timezone.

Is the timezone setting correct? The last three characters in the output line of
```
date
```
And you should have a GUI program to set and check 'Time and Date'. What does it indicate about time and timezone?

Which distro, flavour and version are you running: for example Ubuntu 10.04 LTS or Kubuntu 11.10?

---

### Post by sohmc on 2012-02-03
things ran smoothly after restarting cron daemon.

Not sure what caused the problem but it seems like that cron was reading the time differently.

Oh well...

---

