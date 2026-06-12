---
title: "Sound failure?"
date: 2010-10-06
forum: General Help
---

### Post by heedleblambeedle on 2010-10-06
Every once in a while, sound will fail for an internet application like Google Chrome or Firefox.

There's a fix I found which involves:
sudo lsof | grep pcm
sudo /etc/init.d/alsa-utils restart

But this involves me exiting Chrome and FF. Generally, I have around 50 tabs open in different desktops

Is there a permanent fix for my sound failure?

Computer: Compaq Presario CQ60
Dual core Intel Pentium IV
Sound card: Unknown. Haven't been able to figure this one out

---

### Post by Mr_VeRiTy on 2010-10-06
> **heedleblambeedle said:**
> Every once in a while, sound will fail for an internet application like Google Chrome or Firefox.

There's a fix I found which involves:
sudo lsof | grep pcm
sudo /etc/init.d/alsa-utils restart

But this involves me exiting Chrome and FF. Generally, I have around 50 tabs open in different desktops

Is there a permanent fix for my sound failure?

Computer: Compaq Presario CQ60
Dual core Intel Pentium IV
Sound card: Unknown. Haven't been able to figure this one out
I'm bumping this 'cos one of my other computers does this too, the sound will work fine at first, but then I'll be watching a YouTube video or something and the sound will just quit and wont come back 'till I've rebooted, next time it does it I'm going to see if the OP's method works.

---

### Post by heedleblambeedle on 2010-10-07
shameless bump

---

### Post by heedleblambeedle on 2010-10-07
cmon guys there HAS to be someone out there who has a clue

---

### Post by Mr_VeRiTy on 2010-10-08
> **heedleblambeedle said:**
> cmon guys there HAS to be someone out there who has a clue

Did you try switching to OSS instead of ALSA?

---

