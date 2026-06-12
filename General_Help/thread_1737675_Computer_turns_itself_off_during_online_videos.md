---
title: "Computer turns itself off during online videos"
date: 2011-04-23
forum: General Help
---

### Post by gmolivier on 2011-04-23
While watching online videos, after about ten minutes the computer turns itself off without a warning.  I am new to ubuntu, using v10.10.  This problem is fairly recent, last couple months.  I installed ubuntu about six months ago.

Sound familiar to anyone?  

If you want to give me help, be very basic because i'm not a geek and have only basic knowledge.

Thanks

gmo

---

### Post by Old_Grey_Wolf on 2011-04-23
> **gmolivier said:**
> While watching online videos, after about ten minutes the computer turns itself off without a warning.  I am new to ubuntu, using v10.10.  This problem is fairly recent, last couple months.  I installed ubuntu about six months ago.

Sound familiar to anyone?  

If you want to give me help, be very basic because i'm not a geek and have only basic knowledge.

Thanks

gmo

Is your computer getting hot? Is the fan running constantly? 

You may want to install the Computer Temperature Monitor from the Ubuntu Software Center. Monitor the temperature to see if it is overheating.

If the Computer Temperature Monitor shows over 80 degrees C when the computer shuts off, it is overheating. 

An easy way to install the Computer Temperature Monitor is to enter this command in the terminal ```
sudo apt-get install computertemp
```

That will give us a clue to what the problem may be.

---

### Post by WorMzy on 2011-04-23
Sounds to me like an overheating problem. Next time you're watching a video, open up the System Monitor (or use top), and check the processor usage. If your browser (or plugin-container, or whatever) is using 100%, then you probably have a problem with the version of flashplugin you have installed. If you're using 64-bit, this is a pretty common problem, and there are several versions of flash you can try out to see if it helps.

You can install the 32-bit version of flashplugin and use a wrapper to make it work in your 64-bit browser; or you can use the "stable" version of flashplugin (which is currently 10.2, I believe) which should be in the repos; or you can use the "unstable" 10.3 "square" version of flashplugin by downloading it from the flash website, or by looking on launchpad; or you can use an alternative to flash, called gnash, which should be in the repos.

If your flashplugin seems to be fine, then maybe you just need to take your PC apart and clean out all the dust (using compressed air, preferably), wipe down the fans, and maybe even reseat the CPU's heatsink.

---

### Post by lisati on 2011-04-23
A simpler explanation might be the screensaver: see System->Preferences->Screensaver

---

### Post by Old_Grey_Wolf on 2011-04-23
> **lisati said:**
> A simpler explanation might be the screensaver: see System->Preferences->Screensaver

It could also be the power management options. System -> Preferences -> Power Management.

However, I'm inclined to think it is overheating for some reason. Possibly, like WorMzy posted, a hardware or software problem.

---

### Post by Baumbart on 2011-04-23
I had the same problem from the start. I thought it was normal.
Changing the screensaver or energysaver config doesn't help since they only react to *user* action (mouse or keyboard). So watching a film is "no action" for them.

If that's your problem too, [caffeine]("http://ubuntu-tweak.com/app/caffeine/") should help. If it doesn't, watching the hardware temperature would be my next step also.

---

### Post by gmolivier on 2011-04-23
...thanks everyone, i'll start working on your suggestions

gmo

---

