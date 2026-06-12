---
title: "PC won't stay on... shuts itself off"
date: 2010-06-15
forum: General Help
---

### Post by Grone1985 on 2010-06-15
This is not about Ubuntu but I didn't know where to post it and also thought that there is enough computer savvy people here to help with this... so this is the problem... My desktop PC shuts down by itself without apparent reason and without showing any symptoms before shutting down. I think it is not software related because sometimes it shuts down before even booting the OS.

I cleaned the fan, heatsink and all inside thinking maybe that would help... but no change... I read and think the problem might be with the PSU but also read that the problem could be with the RAM cards for some reason. What is the most likely problem here? Also... A few days ago I noticed that the computer wouldn't turn on if it had been unplugged for a long time and plugged right before turning it on. I had to wait for some 10 minutes and then it booted normally. Any advice? Thanks in advance!

---

### Post by jo4hnc on 2010-06-15
It could be any number of things. What OS are you running? I had a problem several years ago in which my Win XP machine was randomly shutting down. I went through pretty much the same process you went through. I did some research and found articles indicating that it might be a rootkit or some other malware. In the end the problem was a bad USB card. Checking event viewer and doing weeks of different diagnostics led to nothing indicating this. Ont thing you might try is to go to Download.com and look for a free utility called "WhoCrashed" it will show you the memory dump information related to your crash.

Hope this helps.

Edit: You can(assuming you're running windows)go to control panel>system>Startup and Recovery and uncheck automatically restart. This will give you the infamous "Blue Screen of Death that may give you an idea if what caused your machine to crap out.
Another thing you can try is to change your cmos battery if it's an older machine.

---

### Post by Grone1985 on 2010-06-16
Well that is the problem... it doesn't restart, it just shuts down... no warning, no errors, it works normally until it shuts down. I had it running for a while with Everest to see if the temperature went up or something but it didn't so I think it might be a power problem somewhere... Oh yes, it's Windows XP we are talking about here. I checked the voltage sensors on Everest and the one that seemed weird was the +12 which was about 4.5 and while doing the stress test on it it said the computer didn't have a battery.

---

### Post by bodhi.zazen on 2010-06-16
> **Grone1985 said:**
> Well that is the problem... it doesn't restart, it just shuts down... no warning, no errors, it works normally until it shuts down. I had it running for a while with Everest to see if the temperature went up or something but it didn't so I think it might be a power problem somewhere... Oh yes, it's Windows XP we are talking about here. I checked the voltage sensors on Everest and the one that seemed weird was the +12 which was about 4.5 and while doing the stress test on it it said the computer didn't have a battery.

In general, the most common cause of such a problem is hardware, most often over heating.

If you are going to use Windows XP to work through this problem, please ask on a Windows forum.

If you would like to use Ubuntu, perhaps we can help.

---

### Post by PRC09 on 2010-06-16
Maybe try running from a ubuntu live disk for awhile and see if it still occurs....Personal experience with the abrupt shutdown problem was 1. Power supply....2. Blown capacitor on the motherboard....different machines but would work for awhile and then just up and turned off.

---

