---
title: "Setting up a cronjob?"
date: 2010-04-26
forum: General Help
---

### Post by HHx66 on 2010-04-26
I have Flyback installed to continuously backup my /home directory everyday, however, it's not working, what would the command be for it? I have rkhunter working right to update and scan everynight, but this doesn't.

---

### Post by jobix on 2010-04-26
If you don't have a cron job set up, "man crontab" should get you started.

---

### Post by HHx66 on 2010-04-26
I have the job set up, but its not working. I know rkhunter is working as I can check the logs, but flyback will not.

```
5 4 * * * python  /usr/share/flyback/flyback.py --backup-all
```

is what I have entered, is there something wrong with that?

---

### Post by jobix on 2010-04-27
First, I don't know what flyback or rkhunter is.
Second, can you execute the exact command that is in your crontab from the command line instead? Does it work? 

I'm guessing it's got to do with the permissions that are inherited by cron. I can think of two ways to try to figure this out: 
1 - put that line in a script by itself and have cron call the script instead. Inside the script, before calling flyback.py, print the current environment variables into a file (maybe into /tm so that you don't have to worry about permissions.) So, your script might look something like this:
> printenv > /tmp/debugFlyback
python /usr/share/flyback/flyback.py --backup-all


2 - try this and see if it works. In your cron file, at the end of the line add this: "2 > /tmp/errorFlyback" so that it looks like:
> 5 4 * * * python  /usr/share/flyback/flyback.py --backup-all 2>/tmp/derrorFlyback


What you're doing here is redirecting the error into that file in /tmp so that you can go back and take a look.

---

