---
title: "Multiple instances of X"
date: 2006-04-10
forum: General Help
---

### Post by Ian Maxwell on 2006-04-10
I have read in several places that it is possible to run multiple instances of X. I have tried to do so a few times, all with the same result: when I return to the first instance, it freezes so badly that I have to ssh in to kill it.

The two basic methods I've tried are:
- 'startx -- :1'
- altering gdm.conf so that gdm itself opens two instances.

Is there something else I should be doing?

---

### Post by dcstar on 2006-04-10
[QUOTE=Ian Maxwell]I have read in several places that it is possible to run multiple instances of X. I have tried to do so a few times, all with the same result: when I return to the first instance, it freezes so badly that I have to ssh in to kill it.

The two basic methods I've tried are:
- 'startx -- :1'
- altering gdm.conf so that gdm itself opens two instances.

Is there something else I should be doing?[/QUOTE]
Applications-System Tools-New Login

---

### Post by Ian Maxwell on 2006-04-10
Exact same result. In fact, I couldn't even ssh in and had to cold reboot. (This is actually what happened before, too; I had misremembered.)

---

### Post by engla on 2006-04-10
That doesn't sound fun at all.

I don't know much about this, but the problem could very well be driver-specific; you could try another graphics driver and see if the problem stays or not.

---

### Post by Ramses de Norre on 2006-04-10
I have the same problem, when I do ctrl+alt+F7 to get back in the first X session I have only some crippled lines. I can't get into shell mode nor the second X and have to do a hard reset. It happens with all described methods.
I use the fglrx driver from the repo's.

---

### Post by Ian Maxwell on 2006-04-10
Hunh. I also use the fglrx driver; perhaps that is the problem.

---

