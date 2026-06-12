---
title: "Problem with cron"
date: 2010-10-04
forum: General Help
---

### Post by PPPP on 2010-10-04
Hi all,

I have the following cron entry but it doesn't seem to be running:

```
30 17 * * 1-5 /home/usr/main.sh &> /home/usr/log/`date '+%Y-%m-%d'`.log 
```

The script does exist.  And so does the directory /home/usr/log and writable.

/var/log/syslog only has a bunch of these:
```

Oct  4 17:17:01 ubuntu CRON[23107]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  4 18:17:01 ubuntu CRON[23246]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  4 19:17:01 ubuntu CRON[23535]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  4 20:17:01 ubuntu CRON[23688]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  4 21:17:01 ubuntu CRON[24347]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  4 22:17:01 ubuntu CRON[27662]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

I don't see any file gets written to the log directory.  That suggests to me that cron didn't run the job, as confirmed by /var/log/syslog.  What's wrong?

---

### Post by CharlesA on 2010-10-04
Seems cron.daily has a problem running anything that has an extension.

See the thread [here]("http://ubuntuforums.org/showthread.php?t=1585733").

---

### Post by PPPP on 2010-10-04
Weird...okay, I've created a symlink without ".sh".  Let's see if it runs tomorrow.

Thanks!

---

### Post by CharlesA on 2010-10-04
I think you might have to just rename the entire file, but I guess you'll know by tomorrow. :)

---

### Post by john newbuntu on 2010-10-05
Try this:
```
30 17 * * 1-5 /home/usr/main.sh > /home/usr/log/`date +\%Y-\%m-\%d`.log 2>&1
```

---

### Post by PPPP on 2010-10-05
Neither of the suggestions worked :(

---

### Post by PPPP on 2010-10-05
I'm stumped...I tried a test job that just touches /tmp/test.txt and it works.  So is it my syntax?

```
30 17 * * 1-5 /home/usr/main.sh > /home/usr/log/`date +\%Y-\%m-\%d`.log 2>&1
```

---

### Post by CharlesA on 2010-10-05
Yep.

Altho, I'd suggest using $() instead of the backticks:

```
30 17 * * 1-5 /home/usr/main.sh > /home/usr/log/$(date +\%Y-\%m-\%d).log 2>&1
```

---

### Post by john newbuntu on 2010-10-06
So, it looks like cron works although not with your command.  I don't see anything wrong with the commands in posts 7 and 8 since it works for me.  Check your email for any errors by typing 'mail' 

I'd recommend taking it one step at a time.  Start with a crontab as simple as:
*/1 * * * * date > /home/usr/a.log  2>&1
and see if it gets run every minute.  If it does succeed, keep adding the rest one step at a time.

EDIT: Should not matter but my versions are:
Kernel Information: Linux 2.6.32-25-generic i686
GNU bash, version 4.1.5(1)-release (i486-pc-linux-gnu)

---

### Post by PPPP on 2010-10-06
> **CharlesA said:**
> Yep.

Altho, I'd suggest using $() instead of the backticks:

```
30 17 * * 1-5 /home/usr/main.sh > /home/usr/log/$(date +\%Y-\%m-\%d).log 2>&1
```

Changing it to $() works!  Thanks!  :)

---

### Post by CharlesA on 2010-10-06
Is the command now completeing successfully?

---

### Post by PPPP on 2010-10-07
> **CharlesA said:**
> Is the command now completeing successfully?

Yeah, it was working fine yesterday and the day before when I was doing some tests.

---

