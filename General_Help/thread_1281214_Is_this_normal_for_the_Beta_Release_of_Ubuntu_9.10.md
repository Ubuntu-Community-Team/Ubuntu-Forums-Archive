---
title: "Is this normal for the Beta Release of Ubuntu 9.10?"
date: 2009-10-03
forum: General Help
---

### Post by TheNerdAL on 2009-10-03
Okay, So I upgraded to the beta release and I wanted to use update manager but it said that I could not update and gave me a partial upgrade or something, Is that normal?

---

### Post by ackley on 2009-10-03
I've had that happen on 9.04 a few times.

---

### Post by TheNerdAL on 2009-10-03
> **ackley said:**
> I've had that happen on 9.04 a few times.

Okay, Thanks! :D

---

### Post by akakingess on 2009-10-03
Is there a chance that this could also have something to do with which source lists/repositories you have activated (for lack of a better word)? It may be worth looking into those and turning them on/activating them and trying the update again. I only say it may be worth it cuz it doesn't take much time at all and if it works, that would help you out quite a bit.

---

### Post by MaxIBoy on 2009-10-03
If you added third-party repositories that can happen. Also, this happens under normal circumstances too. If program A depends on library B, then library B can't be updated if you happen to also have program A installed, *until* program A gets an update too. It's not really a big deal, the APT software is good enough to auto-detect these problems and suppress the appropriate upgrades.

---

### Post by akakingess on 2009-10-03
Nevermind, I just found [this]("http://ubuntuforums.org/showthread.php?t=1281195") post where someone mentions that the main Ubuntu server will be or is right now distributing 9.10 to all of the mirrors worldwide and could/will cause delays and issues with updates. Hope this helps.

---

