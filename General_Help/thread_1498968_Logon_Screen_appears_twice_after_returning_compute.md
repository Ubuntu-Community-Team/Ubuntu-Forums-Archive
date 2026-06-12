---
title: "Logon Screen appears twice after returning computer from idle"
date: 2010-06-01
forum: General Help
---

### Post by Kerubu on 2010-06-01
Hello,

I've recently done a fresh install of 10.04 on an Acer Aspire 5720 and it went pretty well. However I've a problem with the logon appearing twice.

If I leave my computer idle for too long the screen locks. when I return I'm asked for my password which unlocks the computer but within a few seconds the screen locks again and I need to enter my password for a second time. This time the computer unlocks and stay unlocks.. but it's annoying I have to unlock it twice !

How can I extend the length of time before it unlocks or disable it all together.. until the problem gets fixed?

Thanks

Kerubu

---

### Post by Hammer89 on 2010-06-01
I can confirm this problem. Oddly, though, it didn't start until today despite the fact that I've been running 10.04 for weeks. I don't recall updating or installing anything which would have an impact, either.

And to the original poster: A temporary fix would be to go to the menu (preferences > screensaver) and deselect the "lock screen" option. The problem seems to be related to gnome-screensaver, since I can manually lock the computer and unlock it without this issue occurring.

---

### Post by TheChaos92 on 2010-06-11
I have also had this problem, and I am also running 10.04 on an acer aspire one. I have been running 10.04 for about 4 weeks not and this just started yesterday, I also haven't updated for about a week so this is unusually abrupt.

---

### Post by kyleflan on 2010-06-11
Same problem here. Started happening about 2 days ago. Ubuntu 10.04 here on a Gateway NV. Also, after I enter my password the second time, I have to minimize and then restore whatever window had focus to enter any keyboard input.

---

### Post by dcstar on 2010-06-12
gnmoe-screensaver was recently changed to fix an issue with blank screens after switching log-ons and a side-effect is that it seems to force refresh the unlock screen so you first get the old screen and then it loads a new one that you actually have to use.

This happens in just one second on my PC and I can live with that, but it might just be taking longer on other hardware.

Report it as a bug.

---

### Post by bluepicaso on 2010-08-17
Same problem here. Previously login screen showed me TIME EXPIRED and it refreshes again. now it does not show it. Next time i will try waiting to say it again.

---

### Post by dmelliot on 2010-08-24
Hi
I can confirm this is also happening on two separate laptops both running 10.04.

I am also getting a possibly related problem of my keyboard not working for a few minutes after unlocking.

(Thinkpad T61 & Thinkpad T410s)

---

### Post by martinma on 2010-09-01
Same problem here on an Acer TravelMate 3230. The unlock screen now always appears twice since I upgraded from Ubuntu 9.10 to 10.04. And after unlocking, the keyboard is dead until I change focus to another window, type something there, and then switch back to the original window.

---

### Post by go_beep_yourself on 2010-11-06
Anybody find a solution? This problem is still occuring for me with Ubuntu 10.10. I had the same problem in 10.04. However on my friends laptop, this doesn't happen, and he's running 10.10 through a dist upgrade and wubi.

Has anybody found a bug reported on this issue?

---

### Post by jruberto on 2011-01-21
I had this problem for a long time (on 10.04) and then I don't remember what made it go away.

After last round of updates (or maybe after gicking with screen saver preferences) it is back.

Any thoughts on a resolution?

---

