---
title: "Xorg RAM leakage"
date: 2009-09-02
forum: General Help
---

### Post by Ekeluo on 2009-09-02
Ubuntu (Kubuntu) has been crashing (freeze, kernel panics, etc) on me several times a day now for the past few weeks. Windows vista in contrast is always so nice when ever I have to use it.

Xorg is EATING my RAM. This is not a joke. 5 mins ago, it's RAM usage was 277mb. Now its 460mb. This turns out to about 900k per second. Only Chromium is open. WTF?!

I don't have much time but have to mention this is a dual core laptop with Pentium Dual-Core 1.73ghz, 2gb ram (Now at 533Mb used by Xorg), X3100 graphics. I'm running 2.6.30-10 kernel from X-org edgers repository along with their graphics drivers. KDE 4.3. Please some one help. This is like a time bomb of sorts... (Now 650mb) - Yes I'm a slow typist


Update: Xorg's memory usage passed 1 gig then dropped to its current 210mb. But the rest was not freed. What is going on here????

---

### Post by gradinaruvasile on 2009-09-02
Well i use chromium too and saw an Xorg memory increase... but not that bad as u have it. Its 9 days uptime and Xorg has 284 MB resident mem...

---

### Post by P4man on 2009-09-02
You could perhaps try using a stable kernel, with stable videodrivers running a non alpha browser?

---

### Post by Ekeluo on 2009-09-02
> **P4man said:**
> You could perhaps try using a stable kernel, with stable videodrivers running a non alpha browser?

Well I would, if kde wouldn't run like treacle on them. Really. Also the 'alpha' browser is much faster than any other one I've tried.

---

### Post by shemtovo on 2009-09-02
i seem to have the same problem. and i'm running the regular kernel from the synaptic update.
for me it takes a couple hours for the xorg service to reach 600mb and it stays there until i re start it.

---

### Post by Ekeluo on 2009-09-04
I think this has happened a few times before. Has to do with flash videos (when viewing more than one, I believe) in chromium. Memory usage just climbs and climbs. Well, another reason there's a warning I suppose.

---

