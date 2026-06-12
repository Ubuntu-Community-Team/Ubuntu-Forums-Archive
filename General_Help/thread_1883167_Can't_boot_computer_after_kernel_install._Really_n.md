---
title: "Can't boot computer after kernel install. Really need help!"
date: 2011-11-18
forum: General Help
---

### Post by mlissner on 2011-11-18
I have a Sandy Bridge desktop that was running the stock 11.10 kernel for the past month or so. Every 24 hours or so, it would freeze, forcing me to reboot it. It was pretty frustrating, so today I tried to installed the mainline kernel found here: 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/current/)

This seemed to install OK, so I took a deep breath, and restarted my machine. Upon booting, it's very inconsistent. Sometimes it has a kernel panic, others the kernel just seems to crash. 

I still have my old kernel (the one that worked) installed, but when I try to use it in Grub, it just doesn't work. 

I tried booting from the 64 bit and 32 bit Ubuntu Live CDs, but neither will boot. They too freeze!

Can anybody help me to get my desktop going again? It's my work computer, and I'm at a standstill on my deadlines until it gets fixed. I'm not a happy camper today.

---

### Post by TeoBigusGeekus on 2011-11-18
Did the live cds/usbs use to work? Where and how do they freeze?

Also: working pc and using ubuntu 11.10 is contradictory.

---

### Post by dabl on 2011-11-18
> **mlissner said:**
> 

I tried booting from the 64 bit and 32 bit Ubuntu Live CDs, but neither will boot. They too freeze!



Until I read that, was thinking you were right about a kernel problem.  But booting from a Live CD is totally non-relevant to the new kernel that you installed.  Maybe something else is up with your motherboard or BIOS -- it can't be related to your hard drive or Grub either.

I don't have any experience with Sandy Bridge boards, and there do seem to be some issues with them. In BIOS, do you have any controls related to the video/GPU?  If so, I would try another setting -- the "freeze" is most likely video related.

Also, with your Live CD, did you try the "Safe Graphics" mode?  I think it is F6 on the first text screen?

EDIT:  I don't know whether you saw this or not:  [http://ubuntuforums.org/showthread.php?p=11114284](http://ubuntuforums.org/showthread.php?p=11114284)

This one suggests the original kernel for 11.04 worked with sandy bridge:  [http://osdir.com/ml/ubuntu-bugs/2011-11/msg10264.html](http://osdir.com/ml/ubuntu-bugs/2011-11/msg10264.html)

---

### Post by jonnyboysmithy on 2011-11-18
> **TeoBigusGeekus said:**
> Did the live cds/usbs use to work? Where and how do they freeze?

Also: working pc and using ubuntu 11.10 is contradictory.
He probably means work pc

---

### Post by TeoBigusGeekus on 2011-11-18
> **jonnyboysmithy said:**
> He probably means work pc

That's what I meant too, sorry.

---

### Post by mlissner on 2011-11-18
Solved! Had a bad memory stick. Damn, these things are hard to diagnose.

---

### Post by mlissner on 2011-11-18
Shoot - didn't hit refresh before replying. Thanks for all the help. Totally a hardware issue, though it's so strange that it was working fine before rebooting. So frustrating! Back to work!

---

### Post by jonnyboysmithy on 2011-11-18
> **mlissner said:**
> Solved! Had a bad memory stick. Damn, these things are hard to diagnose.
Great! I'm glad you've got it figured out.

---

### Post by jonnyboysmithy on 2011-11-18
> **mlissner said:**
> Solved! Had a bad memory stick. Damn, these things are hard to diagnose.
Then are you gonna to mark it as solved?

---

