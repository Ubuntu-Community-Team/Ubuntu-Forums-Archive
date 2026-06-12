---
title: "64 ubuntu and kubuntu 10.04 hard lockups eventually"
date: 2010-05-01
forum: General Help
---

### Post by walter_j on 2010-05-01
Im running 64 bit ubuntu and kubuntu 10.04 on a asus i7 mb. After an hour or so i get hard lockups where the only option is to reset or power off. There's no error messages so i have no idea whats the cause. ubuntu 9.10 64 bit has no such issues regarding lockups, so i'm running all three until i figure out what to do.

I'd stick with 9.10 given some changes I detest in 10.04, but liferea and evolution have some bugs that i can't resolve, but they work well in 10.04.

What can I do to find the cause of complete lockups? Is this a common issue in 10.04?

---

### Post by kaligus on 2010-05-17
Until today I would have said it was a one off, however my main machine running Kubuntu has taken to locking up within moments of booting, almost always by the time I have been up for 15 minutes.

---

### Post by soltanis on 2010-05-17
Sounds like a kernel panic, in which case you are going to need kernel logs from your crash.

P.S. Knock on wood, I'm running an Asus i7 as well with 10.04 with no problems. Maybe you should try a clean install? I do use xubuntu, have you tried that?

---

### Post by walter_j on 2010-05-18
xubuntu (16 bit) 10.04 runs w/o lockups for a few days so far. i'm thinking its a 64 bit problem. nothing in logs for my issues. i had system monitor running during one lockup - it wasn't a memory issue, with only 1.4 g of 4 g used. npviewer.bin was using 52 mb though, which seems high. i filed a bug at launchpad.

---

