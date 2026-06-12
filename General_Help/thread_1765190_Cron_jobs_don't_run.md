---
title: "Cron jobs don't run"
date: 2011-05-22
forum: General Help
---

### Post by macho on 2011-05-22
I have this in my crontab (along with another line before it):

```
* * * * * /bin/echo "Does this work?" > ~/test
```

...and the file doesn't show up. I have a blank line after that one in the crontab. I have no /etc/cron.allow or /etc/cron.deny files. I'm running Ubuntu 11.04. /var/log/syslog shows "BEGIN EDIT" and "END EDIT" etc. when I run crontab -e, but doesn't say anything about trying to run commands.

Anything I might be missing?

---

### Post by dcstar on 2011-05-23
> **macho said:**
> I have this in my crontab (along with another line before it):

```
*** * * * *** /bin/echo "Does this work?" > ~/test
```

...and the file doesn't show up. I have a blank line after that one in the crontab. I have no /etc/cron.allow or /etc/cron.deny files. I'm running Ubuntu 11.04. /var/log/syslog shows "BEGIN EDIT" and "END EDIT" etc. when I run crontab -e, but doesn't say anything about trying to run commands.

Anything I might be missing?

And when exactly do **you** think this job will run?

[http://adminschoice.com/crontab-quick-reference](http://adminschoice.com/crontab-quick-reference)

---

### Post by prabbit237 on 2011-05-23
> **dcstar said:**
> And when exactly do **you** think this job will run?

[http://adminschoice.com/crontab-quick-reference](http://adminschoice.com/crontab-quick-reference)

It'd run once a minute, every minute. But that doesn't help with the issue of it not running at all (the same sort of issue I'm having as well.)

---

### Post by JCM_Pico on 2011-05-23
Try making

*** * * * *** /bin/echo "Does this work?" > /home/'youruser'/test
crontab likes the full path of things

---

### Post by prabbit237 on 2011-05-23
I still haven't found a solution that I'd consider "correct" (i.e. that allows a user to run "crontab -e" and get the results to run in cron) but till then I found a work-around. Put the jobs in /etc/crontab (edit it as root...sudo gedit /etc/crontab) and put in the user's name right after the m h dom mon dow fields.

* * * * * [COLOR="Red"]macho[/COLOR] /bin/echo "Does this work?" > ~/test

---

### Post by yetiman64 on 2011-05-23
> **JCM_Pico said:**
> Try making

*** * * * *** /bin/echo "Does this work?" > /home/'youruser'/test
crontab likes the full path of things

Just tested this advice here OP with "crontab -e" and it works, just remember to change 'youruser' to your actual account user name. I copied and pasted JCM_Pico's code and put in my username, went to my home folder and opened the file "test" and it had the contents > Does this work?

---

### Post by macho on 2011-05-23
Thanks for the replies. I tried both including the full path to the destination file, and editing /etc/crontab, including my username. Neither seemed to work for me. Any other thoughts about how I might be able to debug this?

---

### Post by collisionystm on 2011-05-23
> **macho said:**
> Thanks for the replies. I tried both including the full path to the destination file, and editing /etc/crontab, including my username. Neither seemed to work for me. Any other thoughts about how I might be able to debug this?


I suggest you have your cron email you. It will report any errors.

```
sudo crontab -e
```

at the top of your crontab put

```
MAILTO=user@email.com
```

Set your cron to run a minute from now and see what it emails you saying

---

### Post by macho on 2011-05-23
OK, I've figured out the problem, but I'm still not sure how to fix it. The cron daemon doesn't seem to ever get started for some reason. I'll post an update once/if I figure it out.

---

### Post by macho on 2011-05-23
It seems like something's wrong with upstart.

```
sudo status cron
```

...gives no output. Nor does "start cron" nor does "ps aux | grep cron". I'm not sure how to get this working.

---

### Post by collisionystm on 2011-05-23
So just re-install cron


```
sudo apt-get purge cron
```

```
sudo apt-get install cron
```

---

### Post by macho on 2011-05-23
Thanks. I just did as you said and reinstalled cron. Still no luck, unless I need to also reboot or something. I think this might be a broader problem with startup processes since I'm noticing also that when I do Ctrl+Alt+F1, for example, there's no console there.

---

