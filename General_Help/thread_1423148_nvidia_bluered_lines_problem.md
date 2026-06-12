---
title: "nvidia blue/red lines problem"
date: 2010-03-06
forum: General Help
---

### Post by peterl on 2010-03-06
Hello!

I've had a search around but can't find any threads mentioning the problem I'm having. (perhaps my description isn't very good!)

I've attached a screenshot from my desktop showing blue/red lines that appear across most of my screen. The problem gets worse when I scroll, and I've noticed it in evince, firefox and a couple of other programs. When I scroll the lines appear `fixed' on the website or document, and seem to accumulate. 

I've been using compiz with karmic 64 bit... the problem doesn't occur as frequently with metacity, but doesn't go away completely either.

I'm using an nvidia 7600gs. the symptom occurs with drivers 185, 196 (or whatever the latest one is...), 173 and just recently with 96 as well (having rolled back to this one i managed to avoid the problem for a few weeks!).

So I think the problem is something to do with re-drawing... it's worse with compiz, but i don't think that's the cause. the driver I'm using has some effect on the severity of the problem. and I hope that my graphics card isn't broken!

Thanks in advance for any help/sympathy!
peter.

---

### Post by arvana on 2010-03-07
I don't know if this will help, but I've had a similar problem in the past and it turned out to be a physical connection issue with the card terminals.  Try pulling the card, cleaning the terminals if necessary, and reseating it.

Have you had other OS's running on the same machine without these issues?  If so and you're sure it's a 64-bit Karmic issue, try rolling back the Nvidia driver to an earlier version (look in System > Administration > Hardware Drivers). Or try disabling the driver and see if that helps.  Better to do without eye-candy effects than to have lines through your screen!

---

### Post by peterl on 2010-03-09
> **arvana said:**
> I don't know if this will help, but I've had a similar problem in the past and it turned out to be a physical connection issue with the card terminals.  Try pulling the card, cleaning the terminals if necessary, and reseating it.

Have you had other OS's running on the same machine without these issues?  If so and you're sure it's a 64-bit Karmic issue, try rolling back the Nvidia driver to an earlier version (look in System > Administration > Hardware Drivers). Or try disabling the driver and see if that helps.  Better to do without eye-candy effects than to have lines through your screen!

Thanks for getting back to me! I did think that might be it, but two things make me think it's not a (mechanical!) hardware problem. The first is that when the problem isn't too bad, it only appears in certain applications. for example, I've been using my machine for a couple of hours, just opened an evince, and the toolbar is a bit dodgy. Other reason is I've tried removing/cleaning/replacing and it's not made a difference.

No other OS installed I'm afraid... but I've had the card since dapper and this is the first time it's misbehaved!

As for drivers, I'm using 93 now (oldest I can easily get), and it's stable-ish. If I disable the driver the problem goes away... but I think that's because effects are switched off automatically: with the nvidia driver and metacity there's no problem.

I guess I'll just have to hope someone's solved this problem and stumbles across this thread!

p

---

