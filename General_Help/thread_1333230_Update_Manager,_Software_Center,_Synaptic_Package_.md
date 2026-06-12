---
title: "Update Manager, Software Center, Synaptic Package Manager segfault"
date: 2009-11-21
forum: General Help
---

### Post by mynameinc on 2009-11-21
For the last two days, Ubuntu software center, synaptic package manager, nor update manager have worked on my computer (Ubuntu 9.10).  When I try to run any of those, the program appears for less than a second before crashing.  When running software-center, update-manager, or synaptic in terminal, I get the "Segmentation fault" error.  This is very annoying, especially with the bright red triangle (with an exclamation mark in the middle) to the left of the WiFi connection icon.

---

### Post by mynameinc on 2009-11-21
Does anyone have a solution?  It would definitely be appreciated.  Thank you in advance, mynameinc.

---

### Post by jmszr on 2009-11-21
mynameinc,

This worked for me when I had a similar problem:

```
sudo rm /var/cache/apt/*.bin
```

Hope this helps.

---

### Post by mynameinc on 2009-11-21
> **jmszr said:**
> mynameinc,

This worked for me when I had a similar problem:

```
sudo rm /var/cache/apt/*.bin
```

Hope this helps.

It helped, thank you. SOLVED.

---

### Post by yazmonium on 2009-11-28
I was having the same problem.  The fix above worked for me too.

I am running NVIDIA 190.42 drivers and I think they are to blame.  The problem started just after my computer's file system was corrupted -again- by running a Direct X game through Wine.  Does anyone know a permanent fix this problem?

---

### Post by musicman10489 on 2009-12-16
jmszr, 
Thank you so much!!!!
I had the exact same problem and your fix worked perfectly!

---

### Post by Chesamo on 2009-12-16
I know the problem's solved, but in the future remember Synaptic is just a fancy Apt frontend ;)

---

### Post by musicman10489 on 2009-12-17
Yeah I keep forgetting that :]
I'm trying to ween myself off it and ease myself into the CLI.

---

