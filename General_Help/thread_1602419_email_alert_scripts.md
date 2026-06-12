---
title: "email alert scripts"
date: 2010-10-21
forum: General Help
---

### Post by Cyked on 2010-10-21
I'm looking for info/resources on setting up email alerts for things like disk space thresholds, CPU usage, etc.  I also have been playing around with motion and a webcam as kind of a home monitoring system.  

I installed ssmtp and have played with it a bit just sending emails from command line.  After that I started getting emails for cron and anacron for some scripts I have setup in crontab.  

Two of the scripts are for tar files and then delete the originals.  If there are no files to do anything with I get alerts (tar: Cowardly refusing to create an empty archive). They say from root to root as To and From.  I get anacron emails after log rotate runs weekly.  I get an alert about a module not loading successfully for Apache.

With that said of what I have right now, 1) I'm looking for a resource to securely setup the ssmtp file since my gmail password is in the file (I'm using a junk account for now).  I found a site earlier that apparently was a howto on setting up ssmtp securely, but can't find it now and apparently didn't bookmark it.

2) info/resources on setting up various scripts to send alerts if disk capacity/CPU usage reaches some threshold.  And since I am playing around with motion, I'd like to get alerts when motion is actually doing something.  One of the howtos I used when setting up motion gave a script to do this, but I'm not entirely sure what it is meant to be doing, though I do know that it doesn't send emails alerts.

Thanks!

---

### Post by Cyked on 2010-10-22
Anyone?

Thanks.

---

