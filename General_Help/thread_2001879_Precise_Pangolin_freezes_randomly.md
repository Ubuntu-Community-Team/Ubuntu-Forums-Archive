---
title: "Precise Pangolin freezes randomly"
date: 2012-06-11
forum: General Help
---

### Post by ChaseEatsWorlds on 2012-06-11
For a while now 12.04 as been freezing multiple times a day to the point where I have to force shutdown and restart. I noticed that it seems to happen mostly when I am doing things like switching or opening windows. I've never had this problem with older versions and the only change is a new hard drive.
```

-Computer-
Processor        : 2x Intel(R) Pentium(R) 4 CPU 2.80GHz
Memory        : 2051MB (438MB used)
Operating System        : Ubuntu 12.04 LTS
Date/Time        : Mon 11 Jun 2012 06:26:28 PM EDT
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation

```

---

### Post by wojox on 2012-06-11
What graphics card/chip?

```
lspci | grep VGA
```

---

### Post by ChaseEatsWorlds on 2012-06-13
> **wojox said:**
> What graphics card/chip?

```
lspci | grep VGA
```
```
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
```

---

### Post by SheamusPatt on 2012-06-16
I've seem something very similar as well. I suspected Unity (and in fact Unity / compiz does get extremely busy at times for me; Unity 2D is better).  I've switched to Gnome 3, which seems better than Unity but still locks up at times.

Usually, the desktop will free up by itself after a couple of minutes. Yesterday evening, though, it stayed completely frozen for 2 hours (at that point I forced a shutdown).

If I'm listening to music, it's quite obvious that the system has frozen because the music will stop playing.

During this last incident I was running Audacity, which for some reason seems to be prone to this kind of behaviour. Maybe it's due to heavy screen redrawing trying to keep up with a recording on screen (just speculating).

I have an AMD graphics chip
[INDENT][FONT=Lucida Console]01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4250][/FONT]
[/INDENT]  
plus an AMD X3 processor, running in 64 bit mode.

This is very annoying. An suggestions as to how I can help track it down would be most appreciated (I'm quite willing to do some debugging, if that's what it takes).

---

### Post by Curious00 on 2012-06-16
I don't have a solution, but I can commiserate with you. That's the reason I can't use 12.04. I get constant freezes with 12.04. I'm sticking with 11.10, instead. It'll be supported for another couple of years at least, as I understand it. My vga card is an Nvidia GeForce 9800 GT.

---

### Post by seenthelite on 2012-06-16
me too, with Ubuntu 12.04 but not with Kubuntu 12.04. I suspect gnome-shell 3.4.1-Oubuntu2.

```
sudo lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)

```

---

### Post by codingman on 2012-06-16
Lesson 1: Always check Launchpad for bugs before you make a thread here, it is much wiser and you won't waste your time in the forums.

Lesson 2: Make a new thread if you have different specs for a support question, it makes it more distinguishing between two or more people, therefore questions are more easily answered. 

I searched through launchpad and found nothing that matches an exact case like this but there are some bugs that are application specified, and the bug reporter had not realized that this was not only for just that application. I suggest you report this as a bug, there is no hope in diagnostics that would not be potentially fatal to your system, if you do not have a launchpad account, ask someone who does have an account to report it for you (I would be glad to), or you could ask a moderator to do it, most of them have a launchpad account if not all of them.

---

