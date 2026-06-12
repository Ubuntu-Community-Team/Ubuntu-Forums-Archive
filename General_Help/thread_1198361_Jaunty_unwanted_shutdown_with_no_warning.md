---
title: "Jaunty unwanted shutdown with no warning"
date: 2009-06-27
forum: General Help
---

### Post by gldearman on 2009-06-27
Hi, all,

Ever since I've upgraded to jaunty, I've noticed an occasional but serious problem.

Sometimes, Ubuntu will spontaneously shut itself down with no warning of any kind.  I am not talking about a sudden loss of power.  Ubuntu will switch to its normal shutdown screen, shut itself off normally, and power the system down.  The problem is that it does this without me telling it to, and without any warning or countdown!

Thus far, this problem has occurred only when I am using one of two programs: either gThumb or the game Anagramarama.  One of these two programs has always been open and in the active window when these unexpected shutdowns occur. It seems like the computer will turn itself off about 50% of the time when I try to use gThumb, and *every* time I try to play Anagramarama.  The shutdown doesn't happen immediately -- usually, the program in question has been open for about 20 minutes when the computer shuts down.

Has anyone else seen this or a similar problem?  Does anyone have any idea what could be happening?  Is there a system log of some sort that I could check to see how the shutdown command was given?

Thanks, everyone.

---

### Post by credobyte on 2009-06-27
Maybe your video card is not enough powerful and heats up to the maximum ( which could cause this mysterious shutdown ) ?

---

### Post by gldearman on 2009-06-27
Thanks for the answer.

I'm using an nVidia GeForce FX 5200 with 256 MB of video RAM.  I'm pretty sure that it is a sufficient video card (but I'm not real knowledgeable on the subject, so I may be wrong).

I would think that a video card problem would be more apparent on a more video-heavy application.  Anagramarama is a lightweight time-waster desktop game, and all I use gThumb for is browsing my jpeg collection.

---

### Post by Hobgoblin on 2009-06-27
Long shot but..... Maybe a keyboard shortcut you didn't know about?

---

### Post by gldearman on 2009-06-27
> **Hobgoblin said:**
> Long shot but..... Maybe a keyboard shortcut you didn't know about?

Thanks, Hobgoblin.  I don't think that's such a longshot, actually.  I had considered it, since I control both of the offending programs from the keyboard.  But I don't think so, for two reasons:

One, there is no keyboard shortcut for "Shut Down" listed in System > Preferences > Keyboard Shortcuts.  Does anyone know if there are any keyboard shortcuts configured anywhere else?

Two, I seem to remember that, the very first time this had happened, I had stepped away from the computer for five minutes, and I heard the system beep as it shut down.  I'm not 100% sure (since I didn't know I had a problem then), but that would indicate that the system shut down on its own without a keyboard command.

---

### Post by mhgsys on 2009-06-27
Have you checked out if the computer is overheating?

You could monitor you computer temperature and see if that has something to do with it.

---

### Post by gldearman on 2009-06-27
> **mhgsys said:**
> Have you checked out if the computer is overheating?

You could monitor you computer temperature and see if that has something to do with it.

Is there a software way to monitor computer temperature?  Or do I actually have to stick a thermometer inside the box?

Would an overheat cause an orderly shutdown, or just a sudden crash?

---

### Post by mhgsys on 2009-06-27
lol, there is software for that;

open a terminal and type:
```

sudo apt-get install computertemp

```

after that right click a panel, click add to panel and select computer temperature monitor.

ps: 
Could be both I guess, depending on the critical temperature option.
I guess the bios shuts down if the mobo is overheating, If the bios doesn't do this The mobo could suddenly crash, and could burn out.

---

### Post by gldearman on 2009-06-27
> **mhgsys said:**
> lol, there is software for that;


"Yeah, I was joking," he said awkwardly, hiding the thermometer he just got out of the toolbox behind his back ...

Thanks for the software recommendation.  I'll install it and start monitoring.

---

### Post by gldearman on 2009-06-27
By the way, what sort of temperature range should I be looking for?  What is considered too high?

PS: My CPU is an Athlon XP-M 3000+

---

### Post by mhgsys on 2009-06-27
Well, My pc's here are around 40 Celcius in the box, and 49/ 50 on the mobo.
(I guess. all I see is HWmonitor1 and HWmonitor2 )

My laptop did sometimes go up to 65 / 70 degrees, till my fan got broke.
I found out the bios on my laptop shuts it down on 100 Celcius, 

So I would say , on a laptop over 80 is not ok, and on a pc over 65 will get my attention.

---

### Post by gldearman on 2009-06-27
OK, then I think we have found the problem.  My desktop is running 65 degrees Celsius and slowly climbing.   I'll clean out the inside, and, if that doesn't work, take it to a hardware guy.

Thanks for your help.

I think I'm going to shut down now before my computer dies.

Thanks again!

---

### Post by mhgsys on 2009-06-27
Take it to a hardware guy?

Become the hardware guy !

Anyway; Remove the dust, clean the fans, 

Good luck, 
And you could use the computer, as long if it doesn't overheat.
The laptop I was talking about before, (with the broken fan) now runs with a regular fan you can put on the table, 

I just monitor the temperature on it, and turn the fan on max if needed.

(8)

---

### Post by gldearman on 2009-06-28
OK, that was it.  I cleaned the dust off of the fans and the intake.  Someone else had also "tidied" my house, and had obstructed the airflow around the computer; so, I rearranged to fix that.  That did it, and now the computer appears to be maintaining temperatures in the low 50s Celsius.

As far as why the Anagramarama game was causing such high temperatures -- I played the game while running System Monitor.  That simple game puts more load on the CPU than any other application I've seen!  While playing, my CPU load was **constantly** over 95%!  Even running Firefox, Gimp, and half of the Open Office suite simultaneously, I've never seen that kind of load on the CPU!  I'm not sure that I can ever play that game again, even with my computer cooling properly!

Thanks to everyone that helped!

---

### Post by mhgsys on 2009-06-29
Great to hear it's working again.
ps:

As for the game/

[https://bugs.launchpad.net/ubuntu/+source/anagramarama/+bug/328389](https://bugs.launchpad.net/ubuntu/+source/anagramarama/+bug/328389)
[http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg45266.html](http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg45266.html)

It's already been reported.

---

