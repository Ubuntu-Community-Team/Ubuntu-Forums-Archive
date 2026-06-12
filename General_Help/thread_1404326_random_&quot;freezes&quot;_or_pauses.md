---
title: "random &quot;freezes&quot; or pauses"
date: 2010-02-11
forum: General Help
---

### Post by hammergil on 2010-02-11
I am stumped.  I get random "freezes" for like 20 seconds, then back to normal.  Then again the same thing randomly.  I thought it was my hard drive...replaced it, reinstalled 9.10 and same issue.  Thought it might be the memory...nope!, thought it might be my motherboard, tried to update my bios and it froze and now I can't get in to my bios at all.  I bought a new motherboard and did a fresh install of 9.10 and same problem!!!  I took my hard drive out and put it in another computer and it ran the same ruling out hardware issues all together.  Like I said...I am stumped.  anyone help?

---

### Post by xdemo on 2010-02-11
This might not help in your case, but it did for me.
Some applications that spike the cpu usage temporarily cause the screen not to update for some odd reason... in most cases the culprit is compiz.

I managed to fix the 20second freezes by switching to metacity temporarily, eg: watching a movie etc, while i obviously don't want a freeze to occur.

Press alt + F2

Type:
```
metacity --replace
```And to re-enable compiz:
```
compiz --replace
```You should play around with a few things using metacity, and if it fix's the freezing, then compiz is the problem, seems quite common from what i've heard/witnessed. 

Good idea is to add two application launchers with the appropriate commands inside a drawer on your GNOME panel and switch between the 2 depending on what your doing at the time.

Good Luck, :p

---

### Post by hammergil on 2010-02-11
ok, will give a try when i get home from work.  thanks for your help.

---

### Post by hammergil on 2010-02-11
no go.  i started over from scratch.  It seems that the problem is when I load the nvidia graphics drivers 185.  I have a geforce 7600GT.  soon as i uninstall the drivers and reboot, I can surf and do common tasks just fine.  just no 3d and 800x600 res.  It used to work fine and with that driver until now

---

### Post by hammergil on 2010-02-12
any more ideas?  Doesn't freeze real often, but when I play a simple game like N, it is real laggy.  Trying to run a 3d game lags so bad a I can't even exit the game.  Using system monitor, I can see immediately after a 5 second pause, when the system monitor resumes it shows a spike to 99% of CPU usage attributed to gnome-system-monitor.  this is so weird.  using ubuntu for a while now and all of the sudden started behaving this way.

---

### Post by hammergil on 2010-02-12
on another computer, I am running same nvidia drivers with no problems.  Only difference in the machines is the one that works fine has IDE connected hard drive and the one I am having this trouble with is connected with SATA cable.  think there maybe something there?

---

### Post by mk4umha on 2010-02-13
I started getting the same problem after I applied some patch updates to the OS. My orignal 9.10 install had no problems with the GUI pausing.

---

### Post by hammergil on 2010-02-15
found the culprit.  It was my 2-year old geforce 7600GT video card.  I had 3 capacitors that were compromised.  First time I have ever had that happen.  I am surprised the thing even worked.  Anyways, my apologies to Ubuntu because I was starting to question my switch to Ubuntu a year ago.  New video card on the way.

---

