---
title: "schedule updates"
date: 2006-05-18
forum: General Help
---

### Post by marks_linux on 2006-05-18
Is there a simple way to schedule updates in either synaptic or command line using apt?

My ISP has peak off-peak limits so I'd like to make the updates automagically happen through the night for me.

M

---

### Post by Denis on 2006-05-18
In general things can be scheduled using "crontab". It can make a program run at the time specified. Look for more info on the web (e.g. [http://www.adminschoice.com/docs/crontab.htm)](http://www.adminschoice.com/docs/crontab.htm)). 

This should also work with apt-get (it's best to use programs in the terminal). 

make a new cron job: 'crontab - e'
and edit the text like this

0 1 * * * apt-get update
1 1 * * * apt-get upgrade

this will do "apt-get update" every day at 1:00h and "apt-get upgrade" at 1:01h. 
however you need to do this as a **root user**, and I don't really know how to do that with a cron job. 

I'm sure someone else can provide a solution for that.

---

