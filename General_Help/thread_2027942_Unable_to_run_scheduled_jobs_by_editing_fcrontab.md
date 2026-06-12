---
title: "Unable to run scheduled jobs by editing fcrontab"
date: 2012-07-17
forum: General Help
---

### Post by vijaykarla on 2012-07-17
I have installed fcrontab for the user user1. I have a .net web application through which users can schedule the jobs. For this I'm editing the the file "/var/spool/fcron/user1.orig" through c# file operation methods. I'm able to edit the file and I can see the changes by "fcrontab -l" terminal command. But unfortunately the scheduled jobs are not running as they are scheduled in fcrontab.
If I edit the fcrontab through "fcrontab -e" terminal command, the jobs are running as they are scheduled in fcrontab!

I have given read and write permission for the folder "/var/spool/fcron" to the users user1 and www-data and I have no issues editing the file "/var/spool/fcron/user1.orig". Do I need to run anything else so that fcron will notice the changes in fcrontab and so it will rebuild itself?

---

### Post by OM55 on 2012-07-17
It may be that your crontab is incorrect...

To check this out you can try to use the Scheduled Tasks application and schedule a few jobs to see that they are working. You also have the option to put in the regular crontab  string in the advance mode.

To install:

```
sudo apt-get gnome-schedule
```

---

### Post by vijaykarla on 2012-07-17
I have no problem with my crontab. I had my web application working with crontab. But since crontab does not support running jobs on different time zones, I shifted from crontab to fcrontab. I tried adding the users user1 and www-data to the group fcron, but it doesn't work.
here is what I see when I give "fcrontab -l" on terminal
> &timezone(Europe/Brussels) 50	16	*	*	* mono /home/user1/Projects/Project1/CronProcess/bin/Debug/CronProcess.exe 34 d2f45bcd-dcd6-402b-8633-346024b275ae



I am able to schedule this if I edit the fcrontab through "fcrontab -e" and jobs run accordingly.
But If I edit through my c# code (I'm edting the file "/var/spool/fcron/user1.orig"), the jobs are not running at all even though I can see the changes with "fcrontab -l"

---

### Post by Cheesehead on 2012-07-17
Are you saying that the same user-level crontab contains jobs are running and jobs that aren't?
If so, use 'crontab -e' and a minor dummy change to reload and resave the crontab properly.

I'm confused why you changed the permissions on /var/spool/cron/, and why you're directly manipulating the crontabs instead of using the crontab tool for the job. The man pages for both cron and crontab are specific that using the crontab command is required for user-level, manually-created crontabs, and that the crontab program helps users implement crontabs properly. Did you intend to defeat the developer's intent?

Normally, the way to add/remove/edit machine-created crontabs is to put them in /etc/cron.d, not /var/spool/cron. You also don't need to use the crontab command for /etc/cron.d crontabs.

---

### Post by vijaykarla on 2012-07-18
It looks like once you edit fcrontab file, you have to update fcron. There is an option to send the signal by "fcronsighup" which instructs fcron to reread the fcron tables. I tried it but it doesn't works.
Then I came up with idea of having temp file, and edit the temp file rather than fcrontab file and then replace the fcrontab with tempfile through script. Replacing the file through script ensures that fcron will reread modified fcron tables.
Instructions on how to replace fcrontab file can be found here:
[http://fcron.free.fr/doc/en/faq.html]("http://fcron.free.fr/doc/en/faq.html")
(look for **How can I use fcrontab in scripts?**)
And it works!
Thanks for all the helps :)

---

