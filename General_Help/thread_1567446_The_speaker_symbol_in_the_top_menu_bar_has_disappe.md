---
title: "The speaker symbol in the top menu bar has disappeared and I have no sound."
date: 2010-09-03
forum: General Help
---

### Post by Vigh on 2010-09-03
Hi,
 I have been having some difficulties with my sound setup in ubuntu 10.04, everything was working fine, I had attempted to set up ALSA with some success and got it working for my HDMI interface but not my default conexant sound-card, anyway sound was working still for a good time. Then suddenly it stopped working completely. All I did was install a security update yesterday and install aMSN before it stopped working. I was getting an error message come up before boot saying something along the lines of-

"Unknown error- You may experience some problems"

But unfortunately due to it only flashing on screen for a split second am unable to get the full message exactly.

At one stage Ubuntu wouldn't even boot, I ran in safe graphics mode and it worked. So anyway I tried to purge the sound packages and reinstall and now I don't even have the picture of the little speaker on the top menu bar but thankfully Ubuntu is booting successfully. Any advice appreciated.

Anthony

---

### Post by bobcollard on 2010-09-03
Right click the Panel (Menu bar): Add New Items ... Look for "Mixer."

---

### Post by Vigh on 2010-09-03
It doesn't exist in the list.

---

### Post by Vigh on 2010-09-03
Recompiled ALSA sound from source and reinstalled pulse-audio, whatever pulse-audio is lol! Sound is working again.

---

### Post by bobcollard on 2010-09-03
> **Vigh said:**
> It doesn't exist in the list.
Sorry, not running Gnome, it may have a different title?

---

