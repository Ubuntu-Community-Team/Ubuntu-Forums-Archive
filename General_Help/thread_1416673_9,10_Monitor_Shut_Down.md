---
title: "9,10 Monitor Shut Down"
date: 2010-02-26
forum: General Help
---

### Post by smithers3628 on 2010-02-26
I am running Ubuntu 9.10 and i am having trouble with my screen shutting off while I am trying to watch a movie. I have set power management preference to never turn off and i have pulled up the gnome config window and changed the timing manually but it still shuts down. Does anyone have any kind of solution other than changing preferences?

Much appreciated.

---

### Post by ean5533 on 2010-02-26
> **smithers3628 said:**
> I am running Ubuntu 9.10 and i am having trouble with my screen shutting off while I am trying to watch a movie. I have set power management preference to never turn off and i have pulled up the gnome config window and changed the timing manually but it still shuts down. Does anyone have any kind of solution other than changing preferences?

Much appreciated.

Have you been doing system updates? There was a bug in 9.10 that caused the power manager to ignore your settings and just use the defaults, but that bug was patched up a couple months ago.

---

### Post by smithers3628 on 2010-02-26
yeah i actually just updated it yesterday and i think like 2-3 days before that. Still shuts down after 5 minutes.

---

### Post by ean5533 on 2010-02-26
> **smithers3628 said:**
> yeah i actually just updated it yesterday and i think like 2-3 days before that. Still shuts down after 5 minutes.
Interesting, I wonder if there's been a regression again?

I'm guessing you already did this, but just double-check that your screen saver isn't turned on and set to "blank" after five minutes. It should be in the system menu under screen saver (I'm not in front of an Ubuntu machine right now).

If your screensaver is turned off and the power settings are set to not turn off the monitor, I'd recommend filing a bug report. Here's the one that was fixed a while ago, you can file a new one similar to it:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/493645](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/493645)

Good luck.

---

### Post by smithers3628 on 2010-02-26
I didnt even think about changing the screensaver. Talk about stupid. I will have to check it the next time i can run ubuntu (desktop cpu heatsink broke during cleaning yesterday so i not turning on that machine till i get a new one)

Thanks for the idea...now i feel really stupid having not thought of that tho lol.

---

### Post by scouser73 on 2010-02-26
Try Caffeine to keep your monitor on, use these command in Terminal.

> **sudo add-apt-repository ppa:caffeine-developers/ppa**

> **sudo apt-get update**

> **sudo apt-get install caffeine**

Caffeine can be used upto 168 hours & 59 minutes before the screen turns to power saving mode.

I use it on my pc as I was fed up of the screen going black when I was watching a film.

Once installed, Caffeine can be found under Accessories.

---

### Post by ean5533 on 2010-02-26
> **smithers3628 said:**
> I didnt even think about changing the screensaver. Talk about stupid. I will have to check it the next time i can run ubuntu (desktop cpu heatsink broke during cleaning yesterday so i not turning on that machine till i get a new one)

Thanks for the idea...now i feel really stupid having not thought of that tho lol.

That's probably it, then. :p As I recall, the default screen saver is blank screen and the default time is five minutes.

---

