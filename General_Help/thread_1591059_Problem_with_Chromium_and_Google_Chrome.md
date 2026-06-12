---
title: "Problem with Chromium and Google Chrome"
date: 2010-10-08
forum: General Help
---

### Post by marl30 on 2010-10-08
I noticed for a few days now that whenever I start up Chromium it closes immediately once I try to load a website. Google Chrome, on the hand, haven't been starting up at all since the issue with Chromium started. I'm using 10.10. I can't even pinpoint what I installed that caused the problem, as they were both working perfectly at one point. I tried uninstalling and reinstall but that didn't resolve the problem.


Also, does anyone know of a program that groups similar running task in the task area like I see in KDE?

---

### Post by Frogs Hair on 2010-10-08
I would check synaptic package manager for broken packages and try and remember what you may have installed by checking history, also in the SPM.

---

### Post by marl30 on 2010-10-08
I've done a lot of installations over the last few days during the time that I noticed the problem. The only thing I can think of that could have affected them is when I removed the KDE and Edubuntu desktop. I had to manually remove all the related applications for both desktops as well. And there are no broken packages in Synaptic either.

---

### Post by 3rdalbum on 2010-10-08
Remove Chromium's preferences file from your home directory, it sounds like it is corrupted.

---

### Post by marl30 on 2010-10-08
> **3rdalbum said:**
> Remove Chromium's preferences file from your home directory, it sounds like it is corrupted.
Where in home is that located? I selected show all files, but don't any folder for Chromium.

---

### Post by TBABill on 2010-10-08
When I did the upgrade from 10.04 to 10.10 mine would not start up Chromium at all. It would spin as though it were going to load, then just stop. What I found was that the upgrade re-installed the Iced Tea plugin, which conflicts with the Sun Java plugin. Removed the iced tea plugin via synaptic and all was well immediately.

---

### Post by dmillerct on 2010-10-08
Are you syncing your preferences? if so, this might pertain to you:

[http://code.google.com/p/chromium/issues/detail?id=58434]("http://code.google.com/p/chromium/issues/detail?id=58434")

I noticed that after the updates from the daily ppa this morning Chrome failed to execute. It looks like a lot of people are having the same issue. I hope they will patch the issue in the next days' update.

---

### Post by 0N3 on 2010-10-08
I had a similar problem after I installed moonlight plugin on firefox no browser would open for me till I removed the moonlight plugin

---

### Post by marl30 on 2010-10-08
> **0N3 said:**
> I had a similar problem after I installed moonlight plugin on firefox no browser would open for me till I removed the moonlight plugin

Hey, this was the problem. As soon as I removed moonlight plugin, they started working again. Thanks so much!

I still would like an answer for the second question though. Are there any application that will group open windows form running applications as can be done in KDE? :)

---

### Post by 0N3 on 2010-10-09
Not to my knowledge im Gnome user only very little experience with KDE much prefer Gnome

---

### Post by marl30 on 2010-10-09
> **0N3 said:**
> Not to my knowledge im Gnome user only very little experience with KDE much prefer Gnome

It would be cool if someone came up with an apt for it, as I do heavy multitasking and will have many folders open at a time. I wouldn't want to switch to KDE for just this feature, as I'm really not a big KDE fan.

---

