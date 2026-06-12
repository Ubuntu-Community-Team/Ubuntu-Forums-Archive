---
title: "Gnome Scheduler tasks disappeared"
date: 2010-02-17
forum: General Help
---

### Post by lsutiger on 2010-02-17
I walked into my office this morning and noticed that some automated tasks did not take place for the last 2 days. 
So I go to gnome scheduler, and nothing is listed! These tasks have been set to run and have run flawlessly for months!

I went ahead and checked out the tasks under ~/.gnome/gnome-schedule/crontab folder, and they are all listed there (1,2,3 etc).

I really wish I had more clues to give on this, but I do not. 

My question would then be, has this ever happened to any of you out there??

Ubuntu 9.10, completely up to date. 

Thanx in advance

---

### Post by dcstar on 2010-02-17
> **lsutiger said:**
> I walked into my office this morning and noticed that some automated tasks did not take place for the last 2 days. 
So I go to gnome scheduler, and nothing is listed! These tasks have been set to run and have run flawlessly for months!

I went ahead and checked out the tasks under ~/.gnome/gnome-schedule/crontab folder, and they are all listed there (1,2,3 etc).

I really wish I had more clues to give on this, but I do not. 

My question would then be, has this ever happened to any of you out there??

Ubuntu 9.10, completely up to date. 

Thanx in advance

This will show you the commands that cron knows about:

```
crontab -l
```

Check that cron is still running:

```
ps -ef | grep cron
```

---

