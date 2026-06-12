---
title: "Noob needs help with MySql stopping same time once a week"
date: 2010-07-17
forum: General Help
---

### Post by Nacman on 2010-07-17
Hey all,
 
First Post,
 
I am a noob with linux. I am running 9.10 (Karmic). I am running a vbulletin site that acts as a NNTP archive for one newsgroup. I have over 1.4 million messages. I moved it over a year ago from a wamp to lamp box. Never looked back :). However, from some reason, every Sunday morning, generally 7:30 am (plus or minus a few minutes) Something is causing MySql to take a dump. I get the standard vbulletin screen showing a database error has occured when accessing my site from the web. If I go to the machine, stop the Mysql service, restart Apache, restart mysql, all is well till the next Sunday. 
 
I have looked ( noob part) in crontab with nothing showing up except the backup I run on the db on mon,wed,fri. I think I know there may be other cronjobs running but I can't find them ( lack of knowledge where to look). Any ideas, thoughts, help?
 
Nacman

---

### Post by DaithiF on 2010-07-17
Hi, you could have a look at the jobs in /etc/cron.weekly 
nothing mysql related there for me, but yours could be different.

---

### Post by Nacman on 2010-07-17
Thanks for the idea where to look. Unfortunately the only thing in cron.weekly
is something called anacron. Looking into that just in case.

---

