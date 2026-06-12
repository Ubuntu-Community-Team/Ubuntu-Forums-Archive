---
title: "How do I dedicate RAM/swapspace to a process?"
date: 2012-07-10
forum: General Help
---

### Post by J-E-N-O-V-A on 2012-07-10
I've installed a game and it runs well under wine, but when I play it online or if I include bots then it lags quite a lot. I want to dedicate more processing speed to the actual game.

---

### Post by idoitprone on 2012-07-10
> **J-E-N-O-V-A said:**
> I've installed a game and it runs well under wine, but when I play it online or if I include bots then it lags quite a lot. I want to dedicate more processing speed to the actual game.

Changing swap might not do much since
it sound like you have a cpu bottleneck.

wine runs on a single thread which is an issue since we already in the ages of multicore cpus

At best, you can change your swappiness

[https://help.ubuntu.com/community/SwapFaq/#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq/#What_is_swappiness_and_how_do_I_change_it.3F)

As you get closer to zero, it tell the computer to hold the program in swap longer

---

