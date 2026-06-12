---
title: "Need help in scheduling a task to run every 73 minutes"
date: 2011-05-24
forum: General Help
---

### Post by Natanael on 2011-05-24
I was searching for many time but haven't found any solution. 

Cron would be great, but it allows only steps in range 1-59 minutes.
Is there any mode to run something exactly every 73 minutes?

The second i need (the same problem) to run program little more than every 12 hours, it might be in steps of 12 hours and 4 minutes (but 13 hours is much too much).

Can anyone help?

---

### Post by Gakumerasara on 2011-05-24
I'm not a Linux expert, and there's probably a better way to do this, but here's what I would do...  Using a Bash script:

```
#!/bin/bash
while [ 1 ]
do
   [command to run your program]
   sleep 73 m
done
```

You could either run this script yourself in the background or, if you prefer, have it run automatically when the computer boots by placing "/bin/sh /path/to/script.sh" into /etc/rc.d/rc.local

hope this helps!

---

### Post by SecretCode on 2011-05-24
It does seem that cron by itself will not help you do this.

If you don't want a long running shell script like the above (in case it's terminated for some reason - there would not be a performance issue), other options might be to restart the timer at the end of whatever program you need to run at intervals, either by writing a one-shot crontab entry or (possibly better) using **at **(see _man at_).

Either of those cases would require superuser rights, unless you have a user account to run this in that is guaranteed to stay logged in.

Yet another approach would be to have a manager job run via cron **every minute**, and have this job increment a counter or check the time since a last-run timestamp (counter and timestamp would have to be stored in a file), and run the desired program if 73 minutes / 12h4m have passed. I like this idea - the performance hit of checking every minute should be neglible and security can be nailed down.

---

### Post by Natanael on 2011-05-27
Wow, thanks for your fast replies. Hm... your ideas are really cool, I didn't thought about. 

The idea with easy script loop is good (thanks Gakumerasama), but in my case it may be problem if i put it in rc.local - because it's program with gui. 

And yet - the computer is turned off for night - in the second case (the program which should run every 12h and 4 minutes). In the case, it should be run during this off time, the program should run on computer startup and timer set to +12:04h from actual time.

The second idea seems more applicable in my case. I will try to do something... but I'm not very good in scripts.

To be honest I've had a hope, theres any tool for Ubuntu with GUI I do not know, which could do this. Thought it's popular need for users. Was very surprised that cron doesn't allow this (tried with Ubuntu gui, after it checked in cron man).

So I see I will have to make some good script... The problem is when computer is turned off (or restarted) - when it goes on, he should know how much time he should wait yet to run the program. 

The idea with every minute run script is good start I think in searching solution. If you could give me some more ideas would be great.

Really thank you for replies.

---

### Post by SecretCode on 2011-05-30
> **Natanael said:**
> To be honest I've had a hope, theres any tool for Ubuntu with GUI I do not know, which could do this. Thought it's popular need for users. Was very surprised that cron doesn't allow this (tried with Ubuntu gui, after it checked in cron man).

Do you think it's a popular requirement? I can't think of a case where I would have needed it. Why is it important to you?

It should be a fairly simple case to start learning BASH scripting from :)

---

