---
title: "Freezing on Karmic"
date: 2009-12-30
forum: General Help
---

### Post by slickback on 2009-12-30
Sorry, i am a noob to all of this so please excuse me. i recently installed 9.10 karmic koala on my 5 year old computer which had previously been running windows xp. Ubuntu runs fine, except for It will randomly crash into sometimes a screen with a white background and several vertical bars, sometimes into a brownish screen with a little box of bars, and a white screen with a little box of bars in the left hand corner. I have a AMD 64 and and ATU radeon express 200, how can i fix this?

---

### Post by MooPi on 2009-12-30
Sounds suspiciously like a graphics card failure. How often does this happen and are you doing anything special when it happens? I'm guessing from the specs that your using a laptop?

---

### Post by slickback on 2009-12-30
nope, its an emachine desktop. it happens almost every time i use it. sometimes a few minutes after i start my system or 45 minutes afterwards. i have to do a power cycle to fix it.

---

### Post by iloveunix on 2009-12-30
First UNMOUNT all drives, discs and filesystems. Then open a terminal and type-

   (sudo) fsck -(f)y

 (Sudo if your not the root, and f- flag if journalling is on)

  Fsck scans your systems for glitches, and automaticly fixes it.
  It should fix ur problem. REMEMBER! REMOUNT ur discs etc before shutdown! ,uatilus will crash if u don't!


     If this doesn't work, call proggrammer, or reinstall ubuntu.

      Good luck.

---

### Post by MooPi on 2009-12-30
Do you feel comfortable opening the case of you computer. Always unplug before doing this. Inspect for excessive dust and clogged heatsinks and ventilation. I suspect heat is an issue and may be the cause.

---

