---
title: "scripting unattended updates"
date: 2009-10-27
forum: General Help
---

### Post by shwallace on 2009-10-27
I'm trying to make a script to run from gnome scheduler that will process all my updates during certain hours of the night. I've been using:

sudo apt-get update

The problem is that sudo requires a password and I'm not going to get out of bed at 2:30 in the morning to run my updates.

Does anyone know how to run sudo apt-get as root without having to manually enter a password?

---

### Post by undecim on 2009-10-27
You can turn on automatic update through the "Software Sources" program

---

### Post by alphaniner on 2009-10-27
I don't know anything about gnome scheduler, but I have used root's crontab to automatically do updates.

FYI with the upgrade command, you will need to use the -y flag:

```
apt-get -y upgrade
```

---

### Post by shwallace on 2009-10-28
Thanks for the help folks! I've looked at the automatic update feature but it doesn't seem to allow me to set the time for update. My ISP limits my download except between 2 and 6 AM. I need my large download to run during that time. I've tried making a root crontab but don't seem to be getting anywhere with it. Maybe I should do some more research on crontab!

---

### Post by QLee on 2009-10-28
[QUOTE=shwallace]... My ISP limits my download except between 2 and 6 AM. I need my large download to run during that time. I've tried making a root crontab but don't seem to be getting anywhere with it. Maybe I should do some more research on crontab![/QUOTE]

Yes, learn all you can so that you will understand anything that someone suggests you do, before you do it.

Show what you tried and someone probably can suggest changes that will work. It won't hurt to tell what happened (and didn't happen) with what you already tried.

Note: You do realise that "apt-get update" will only update the packages available, not automagically "upgrade" your system, don't you?

---

### Post by shwallace on 2009-10-28
I know the diff between update/upgrade. I was testing with update because it doesn't download enough to bust my limits. I'm still reading up on crontab, ap-get, and bash! Loads of fun:)

---

### Post by QLee on 2009-10-28
> **shwallace said:**
> I know the diff between update/upgrade. I was testing with update because it doesn't download enough to bust my limits. I'm still reading up on crontab, ap-get, and bash! Loads of fun:)

I understand, just wanted to make sure.

I like the approach you are taking, teaching yourself and not asking anyone to *do* the job for you. Almost anyone here is willing to help someone who just needs a suggestion or small correction.

alphaniner gave you a good hint. Remember to "update" before you try "upgrade".

---

### Post by shwallace on 2009-10-28
Ok, here's the latest. I did a sudo crontab -e. I made an entry for: apt-get -s mhwaveedit >outputfile. The outputfile indicated a successful test. I modified the entry like this: apt-get -y install mhwaveedit. The syslog entry is:
Oct 28 12:10:01 steve-u91 CRON[2040]: (root) CMD (apt-get -y install mhwaveedit)
Looks to me like it worked only no mhwaveedit on my machine! Any ideas what went wrong?

LATEST UPDATE: the deb pkg is on my machine in the /var/cache/apt/archives, but it's not installed.

---

