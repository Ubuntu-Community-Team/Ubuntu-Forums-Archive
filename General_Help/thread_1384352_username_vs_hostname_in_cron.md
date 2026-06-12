---
title: "username vs hostname in cron"
date: 2010-01-18
forum: General Help
---

### Post by rlambkin on 2010-01-18
Somehow, I changed my user name and screwed up ability to run cron tasks. Username was myname-main before I changed it. Currently, I show this:
$ username => myname
$ hostname => myname-main

I try to do a sendmail with cron and get these errors in log:

myname-main sm-msp-queue[3209]: My unqualified host name (myname-main)  unknown; sleeping for retry

myname-main sendmail[3211]: My unqualified host name (myname-main) unknown; sleeping for retry

myname-main sm-msp-queue[3209]: unable to qualify my own domain name (myname-main) -- using short name

myname-main sendmail[3211]: unable to qualify my own domain name (myname-main) -- using short name

How do I change username back to myname-main?

---

