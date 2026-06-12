---
title: "Cached RAM?"
date: 2010-07-26
forum: General Help
---

### Post by physic.dude on 2010-07-26
I play a game called Garry's Mod (Half Life 2 mod) through Wine and I have noticed after a few minutes of the running the game my cached memory, seen on the system monitor on a panel, builds up and suddenly the game starts lagging. This happens even when no props or objects are spawned. (EXTREMELY annoying)

If anyone could help me that would be great.

---

### Post by MaxIBoy on 2010-07-26
Well, any memory which is currently unused will be used as cache to store commonly-accessed files. This speeds up overall system performance. Remember, unused RAM is wasted RAM-- you want your RAM usage close to 100% at all times.

The best explanation I can think of is that whenever the games starts lagging, it uses less RAM, so more is available for use as cache. Or something. Anyway, it's certainly not the cache which is causing your performance issues.

---

### Post by physic.dude on 2010-07-26
The same thing happens even when I have ALL graphic settings in the game set to low (i.e. texture detail, anti-lasting, exc.) 

Any more ideas?


My second guess would be compiz since it is usually third or fourth after the game engine and Wine for memory usage. Any settings there I can change?

---

### Post by MaxIBoy on 2010-07-26
There's your problem. If you run Compiz at the same time as a graphically-intensive game, the two will fight over your graphics card. Install the fusion-icon applet, it will allow you to switch back to a non-compositing window manager temporarily for gaming.

---

### Post by physic.dude on 2010-07-26
> **MaxIBoy said:**
> There's your problem. If you run Compiz at the same time as a graphically-intensive game, the two will fight over your graphics card. Install the fusion-icon applet, it will allow you to switch back to a non-compositing window manager temporarily for gaming.


Dumb question: How do I get that fusion-icon applet up? I just installed it.

---

### Post by physic.dude on 2010-07-26
> **physic.dude said:**
> Dumb question: How do I get that fusion-icon applet up? I just installed it.

Never mind I found it...

.

---

### Post by physic.dude on 2010-07-26
Actually the game still lags a few minutes in.   :evil:

---

### Post by MaxIBoy on 2010-07-26
Did you switch to a different window manager, like Metacity? Should look something like the attached screenshot.

---

### Post by physic.dude on 2010-07-26
> **MaxIBoy said:**
> Did you switch to a different window manager, like Metacity? Should look something like the attached screenshot.

Yup, but that didn't work. 
Nothing is taking a lot RAM usage other then the game itself with about 1 gig. (Out of 4gb)

Any more ideas?

---

### Post by physic.dude on 2010-07-27
Is there any settings within the game or system that you recommend I change?

---

### Post by physic.dude on 2010-07-27
anyone, Bump?

---

### Post by physic.dude on 2010-07-28
Need help still

---

### Post by linux18 on 2010-07-28
wine uses open gl and a converter between directx and open gl.....

actually I have no clue, do it with openbox

---

