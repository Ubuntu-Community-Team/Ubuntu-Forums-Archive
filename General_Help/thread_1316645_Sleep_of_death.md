---
title: "Sleep of death"
date: 2009-11-06
forum: General Help
---

### Post by kumoshk on 2009-11-06
I've noticed that ever since I started using Ubuntu, with every version of it, on every computer I've used it on (except maybe one), my computer will go to sleep, but it'll never wake up again.

To get my laptop working again, I have to take the battery out and put it back in&#8212;or else I just have a black screen with a humming computer forever, even if I hold down the power button for the desired length of time.

Is this normal behavior? I've just avoided using the feature since it seems so universally unusable for me. I don't know why I never looked for a fix until now.

Is there a common workaround?

The same or similar stuff probably happens with hibernation. As you can understand, I'm reluctant to test and retest the issue time and again to refresh my memory without knowing that it will help somehow. (Most of the times I've 'tested' this feature have been by accident.)

Currently, I'm using Karmic (64-bit) on my laptop: it's a Compaq Presario CQ60-212US Notebook PC (4GB RAM, nvidia video card, etc.)

Anyway, I'm happy using Ubuntu even if I can't get this working (I've never been in the habit of putting computers to sleep much)&#8212;but it would be nice, still, and I'd rather not feel too out of place around everyone else with properly sleeping computers.

---

### Post by Niniel on 2009-11-06
I have no idea what to do, but my 9.04 desktop tends to do the same - I go away, the screensaver kicks in, and then after some time (sometimes sooner, sometimes later, and sometimes not at all even after a long time) the system won't come back and I have to do a hard reset. 
I've taken to not leaving the computer on when I'm not using it.

---

### Post by Duskao on 2009-11-06
Just so you guys know, it's generally a better idea to turn off your laptop when not using it. They are not meant to last forever and laptops are prone to over heating. If you turn them off when not in use it will prolong the life of the computer. A laptop is not a PC, and even PC's should be shut down or put into suspen/hibernate when when in use.

---

### Post by kumoshk on 2009-11-06
> **Duskao said:**
> Just so you guys know, it's generally a better idea to turn off your laptop when not using it. They are not meant to last forever and laptops are prone to over heating. If you turn them off when not in use it will prolong the life of the computer. A laptop is not a PC, and even PC's should be shut down or put into suspen/hibernate when when in use.

I already do most of the time. Mine does get quite hot if its doing something, but that's not the only reason I do it. I have disabled the automatic go-to-sleep stuff, though.

Niniel, I would suggest altering your power settings to remove the sleep actions, and/or replace those you can with shutdown ones. Go to system-->preferences-->power management. Look at the options.

---

### Post by Niniel on 2009-11-06
Just so that you know - a laptop really is a PC! 
It certainly is not a toaster!

Besides, I have the problem with my desktop PC. 
And the issue is that the computer is not waking up from sleep, so suggesting to put it into sleep is, well, shall we say, not very helpful. :)

---

### Post by kumoshk on 2009-11-06
I've had similar problems on one or two desktops before, too.

---

### Post by Niniel on 2009-11-06
> **kumoshk said:**
> Niniel, I would suggest altering your power settings to remove the sleep actions, or replace them with shutdown ones. Go to system-->preferences-->power management. Look at the options.
Thanks, but that would not do me much good. Burning CDs on my external drive can take a while, and shutting down in the middle of it wouldn't be so great. :)
But maybe I need to disable the screen saver...

---

### Post by kumoshk on 2009-11-06
> **Duskao said:**
> Just so you guys know &#8230;

Speaking of computer life-span, whatever happened to the options for turning the hard drive off after the computer is idle so long? Was it just too annoying or something? I know I hated how that worked in Windows, anyway.

---

### Post by kumoshk on 2009-11-06
> **Niniel said:**
> Thanks, but that would not do me much good. Burning CDs on my external drive can take a while, and shutting down in the middle of it wouldn't be so great. :)
But maybe I need to disable the screen saver...

Heh, heh. Yeah, you rarely know when a program keeps you from going idle. I think the shutdown option only exists for closing the lid, though&#8212;but on a desktop I guess you don't have a lid, so I'm not sure what happens there. I'd just disable all the sleep options.

---

### Post by Duskao on 2009-11-06
My apologies, I missed the second post where it is mentioned about the Desktop PC. There was no need to be rude as I was only offering the information I could to try to help you out. My point was that if you leave your laptop on all of the time you are asking for trouble ie. cpu/HD/gpu/RAM could all potentially overheat and cause issues to your computer/motherboard. 

As was mentioned, it is likely a good idea to disable the screensaver as a lot of them use the cpu/gpu which could cause an overheat and crashing your computer if left on for extended periods of time without proper airflow and cooling which most laptops lack. It could be something more internal with your drivers or hardware incompatibilities. 

Sorry I can't be of more help. Best of luck.

---

### Post by kumoshk on 2009-11-06
> **Duskao said:**
> My apologies, I missed the second post where it is mentioned about the Desktop PC. There was no need to be rude as I was only offering the information I could to try to help you out. My point was that if you leave your laptop on all of the time you are asking for trouble ie. cpu/HD/gpu/RAM could all potentially overheat and cause issues to your computer/motherboard.

It's all right. I don't think any rudeness was intended (and certainly not on my part). Sorry if it came off that way. Thanks for the advice.

---

### Post by dvlchd3 on 2009-11-06
I still feel this thread is unresolved.  I have had this same issue since at least 9.04 (perhaps 8.10...)

I frequent a coffee shop, and end up getting in many conversations and away from my laptop for sometimes an hour or more (damn politics!).  I'd prefer to have it go into "suspend" to conserve battery/etc.  However, since my computer never wakes up, this is not possible.  To change the settings to shutdown, would just make it annoying to come back to a powered off laptop, possibly having me lose some work. (I'm pretty good about saving often, but hey, sh** happens...)

Does anyone have a solution/bug report for this issue?  I haven't done much searching, just happened across this thread...

---

### Post by marmida on 2009-11-06
I think this is a pretty standard problem; integration of ACPI and kernel stuff necessary for suspend/hibernate has always been pretty rough.  I am having problems with 9.10 not waking up out of sleep (hibernate works fine).

When I have some time, I'm going to dig through /var/log/messages looking for some useful info on what's going on during shutdown and resume.

---

### Post by mitchellcipriano on 2009-11-07
I had no problems with suspend/resume in 9.04 and prior. I have 9.10 running on a desktop with no problems. I upgraded my note boot from 9.04 to 9.10 and now suspend does not work. There is another threat on this topic at: [http://ubuntuforums.org/showthread.php?t=1307618&page=15](http://ubuntuforums.org/showthread.php?t=1307618&page=15), but there is no real resolution. From the number of people reporting that resume worked prior to moving to 9.10 it looks like a regression.

---

### Post by kumoshk on 2009-11-07
Ah, I just wanted to point out that none of my cited installations of Ubuntu have been upgrades (all fresh installs), if that makes a difference.

---

