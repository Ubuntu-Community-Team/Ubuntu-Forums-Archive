---
title: "Lucid x freezes on eee"
date: 2010-05-08
forum: General Help
---

### Post by frrobert on 2010-05-08
Sorry about another thread about this but I have not seen a fix posted yet.

I am running Lucid standard Ubuntu on 1000HA with Intel GMA 950 graphics.

I periodically have keyboard and mouse freezes.  It seems turning off visual effects decreases the frequency of the problem but does not solve it.

I turned on the keyboard map of control-alt-backspace and I am able to restart x when it freezes.

I am running kernel 2.6.32-22-generic which if I read things correctly includes fixes for x memory leaks.


thanks in advance

---

### Post by squirrel_chaser on 2010-05-08
I am having the same problem on a MSI Wind PC with Intel GMA 950 integrated video.  The machine will freeze about 15 minutes after startup everytime.

Sorry, I have not found a fix.

The good news is that Debian Squeeze works great on the same machine and Lucid is working great on my Dell laptop.

---

### Post by frrobert on 2010-05-10
I found turning off compiz decreases the frequency of lockups.  I ran for almost 2 days before x froze again.  I looks looks like both lucid and squeeze use the same version of the intel video driver, but if I read the version numbers righte it looks like squeeze uses a slightly newer version of xorg core.

---

### Post by devicerandom on 2010-05-11
I have freezes on the 1201n, with Lucid. It seems more of a kernel panic -sometimes (not always), the caps lock light blinks, which AFAIK is a kernel panic symptom.

It seems related to network activity -stuff like using KTorrent or other network-intensive stuff increases the problem, but it's very erratic.

Any hint appreciated.

---

### Post by anoe on 2010-05-20
and how do u turn compiz off? turning off visual effects?

---

### Post by frrobert on 2010-05-20
Go to System Menu

Select Preferences -> Appearance 

Once the window opens click on the Visual Effects

Select None and then hit the close button.

This will turn off compiz.

Hope this helps.

---

### Post by anoe on 2010-05-20
hi there, i installed compiz config settings manager (maybe it was already installed with karmic) and in preferences i unchecked 'integrate with desktop'. Not sure what it does, but up to now it seems it's working better, and the visual effects are still running.

i'll keep u up to date, tx for the tip.

---

