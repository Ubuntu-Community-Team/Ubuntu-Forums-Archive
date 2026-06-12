---
title: "Automate tasks"
date: 2012-08-17
forum: General Help
---

### Post by sbnsbn on 2012-08-17
Sorry if this has already been answered but I could not find it.  I have an old ASUS 900A eeepc and want to use it with Pandora radio.  I am looking to have it start automaticly at a predetermined time every day, play the same station for maybe 4 hours, turn off for a few hours, then turn the station on again for a few more hours.  I want this to happen every day.
There has to be an easy way to set this up but what I have found so far seems complicated for a newbie.  Is there any easy way to do this.  I plan to leave the eeepc on all the time but will need it to wake up when needed.
Anybody have any suggestions?
Thanks

---

### Post by Habitual on 2012-08-17
[Turn your computer into a digital radio alarm clock]("http://forums.linuxmint.com/viewtopic.php?f=213&t=77603&p=459886")

HTH.

---

### Post by Cheesehead on 2012-08-17
> **sbnsbn said:**
> I plan to leave the eeepc on all the time but will need it to wake up when needed.

If the system is asleep, no processes can run to wake it up. You must leave the system on (awake) duing your sleep for this to work.

There are several ways to do this: For a new user, go into the Power Manager and change the settings so that closing the lid doesn't suspend the system. This may have unintended consequences during the day, since your system won't sleep when you close the lid anymore - you must manually suuspend it. For a more advanced user, use dbus signals to inhibit suspend at night and resore the functionality during the day.

---

### Post by rukiaEnix on 2012-08-17
Try with CRON is really easy.

If you type this command:

```

crontab -e

```

If it's the first time you use it then it will ask what text editor do you want to use to add the jobs. I recommend to choose nano as it is easier.

It will open a file to add the jobs, it also has the instructions on how to do it at the top of the document.

---

### Post by sbnsbn on 2012-08-19
Hate to sound lie a real newbie, but I cannot figure out how to start up cronon ubuntu 10.04. Can anybody help directing me to open cron, then wrtie a script to turn on and off pandora radio every day at a certain time.

---

### Post by llamabr on 2012-08-19
> **sbnsbn said:**
> Hate to sound lie a real newbie, but I cannot figure out how to start up cronon ubuntu 10.04. Can anybody help directing me to open cron, then wrtie a script to turn on and off pandora radio every day at a certain time.

The instructions that 'habitual' gives above look quite useful.  Maybe start there.

---

### Post by rukiaEnix on 2012-08-20
If you just execute crontab -e you will see instructions there...

---

### Post by sbnsbn on 2012-08-22
Like I said, I am a real newbie with ubuntu.  how do I type "crontab -e" into ubuntu?
Do I use terminal (does not seem to work) or some other method to actually get the command to work. Any help please.

---

### Post by rukiaEnix on 2012-08-22
Yes, it is with terminal.... and you just type it.

---

