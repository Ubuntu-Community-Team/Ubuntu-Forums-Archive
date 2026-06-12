---
title: "Laptop can't finish"
date: 2010-06-21
forum: General Help
---

### Post by Don DeGregori on 2010-06-21
Regarding 10.04. No problem loading and installing on 2 desktops. No problem loading prior versions, 9.10 on my older Fujitsu laptop. But, can't get 10.04 to get past the moving dots. When the dots end, I see a flash of a few little bars of color in center of screen for a second, and then just a salmon colored screen and no more disk or CD activity. The load justs quits. I wait and wait 5 minutes, nothing. Wiped the CD, tried again, no joy. Tried CD on another computer with 10.04 already in, no problem, the load continues to the end. Please help. The laptop is a Fujitsu is P5010D. It now dual boots XP and 9.10. It just doesn't like 10.04. Is there an Alternate CD available? Probably, something with laptop video. Never seen this before with Ubuntu.
Don

---

### Post by plucky on 2010-06-22
> Is there an Alternate CD available? 

Yes [Here](http://releases.ubuntu.com/lucid/)

Good Luck

---

### Post by Don DeGregori on 2010-06-23
Thanks, plucky

Well, I did what you suggested and downloaded Alternate Ubuntu 10.04. This did work and I got through the install. Even brought in all the 189 updates. But, can not boot except in "recovery mode" and choosing failsafeX. This is the choice that works.Then, I see box saying Ubuntu is running in low-graphics mode. I click OK. Then I see a box "what would you like to do" I choose "run Ubuntu in low graphics mode for just one session" There are 4 other choices. I click OK. This is the choice that works.The boot continues OK with a few abnormal colored flashes and Ubuntu audio theme a bit choppy. Then, I notice under System, preferences, Monitors that monitor is unknown and Refresh rate is 0 Hz. Resolution is 1024 x 768. Other choice is 800 x 600, and shows 60 Hz. This choice messes everything up. Total horizontal out of sync. Have to restart. Restarting or Shutdown does work, but with lots of abnormal color flashes,too.

This reliable laptop has worked just fine till 10.04! I think I can send in the error log from the Recovery choice.

Anyone else have some good things to try?

Don

---

### Post by Harvey Yebubbleman on 2010-06-23
Have you had any better luck with Linux Mint?  I tried version 9 which, I guess had Ubuntu 10.04 at its core and had the same problem.  I had your same problem with stock Ubuntu 10.04 and am now having your same wireless problem with Ubuntu 9.10; it helps to have the same exact computer!  That said, I'm considering doing one of the following: either (a) scrapping this installation and going to Linux Mint 8, (b) attempting your wireless fix and see if I can then upgrade successfully to 10.04 or (c) trolling the Linux Mint forums to see if anyone there with our mutual laptop has gotten that to work.  And all this time, I thought that my Early 2006 Core Solo Mac mini would be the most glitchy 32-bit x86 Ubuntu machine I've had the pleasure of working with, though I think the P5010D beats it.  In any event, I'll keep this thread posted.

---

### Post by bollix47 on 2010-06-23
> **Don DeGregori said:**
> Then, I see box saying Ubuntu is running in low-graphics mode. I click OK. Then I see a box "what would you like to do" I choose "run Ubuntu in low graphics mode for just one session" There are 4 other choices. I click OK. This is the choice that works.The boot continues OK with a few abnormal colored flashes and Ubuntu audio theme a bit choppy. Then, I notice under System, preferences, Monitors that monitor is unknown and Refresh rate is 0 Hz. Resolution is 1024 x 768. Other choice is 800 x 600, and shows 60 Hz. This choice messes everything up. Total horizontal out of sync. Have to restart. Restarting or Shutdown does work, but with lots of abnormal color flashes,too.

Anyone else have some good things to try?

Don

Have you tried going into System>Administration>Hardware Drivers to see if anything is suggested and if so try activating it?

---

### Post by Don DeGregori on 2010-06-24
> Have you tried going into System>Administration>Hardware Drivers to see if anything is suggested and if so try activating it?

Fujitsu needs a B43/legacy wireless driver and asks to install it. Ubuntu has it and installs fine. No other drivers show up.

---

### Post by Don DeGregori on 2010-06-24
> Have you had any better luck with Linux Mint? 


Thats an idea. I'll try it. Thanks

---

### Post by Don DeGregori on 2010-06-24
> **I tried version 9 which, I guess had Ubuntu 10.04 at its core and had the same problem.**

I overlooked about that you said Mint 9 didn't work. I have Ununtu 9.10, and very little else in the Fujitsu now. I'll see what happens when I try an upgrade to 10.04. I usually don't do upgrades and start fresh.

The P-5010D was ahead of it's time, a good laptop. I've tried "everything" on it. First time such a such fatal error, not wanting to boot a LiveCD. WHAT HAVE THEY DONE!

---

### Post by Don DeGregori on 2010-06-24
[B]Well, this time I did upgrade to 10.04 on 9.10. Still no joy. I'm done with 10.04 on this good laptop, a Fujitsu P-5010D! All other prior distros of Ubuntu work on it. Launchpad people, please note.

:confused:    Don[/B]

---

### Post by Harvey Yebubbleman on 2010-06-26
I'm using Linux Mint 8.0, which is based on Ubuntu 9.10.  It runs just fine, abeit a little slow; this thing could use more RAM for sure.  For now, I'd say that this is the best form of Linux I could do for this comp without looking into a more lightweight distro or ordering more RAM.

---

