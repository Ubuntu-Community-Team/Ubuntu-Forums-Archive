---
title: "Playing MMORPG using WINE and getting no sound."
date: 2011-10-22
forum: General Help
---

### Post by Ladders on 2011-10-22
I'm not sure if this is in the right forum, so please bear with me.

I play an MMORPG, Champions Online, and to do so I obviously installed WINE, then Internet Explorer 8 followed by the game itself. This all worked just fine on 11.04. With 11.10 recently released I upgraded. The game still starts and loads properly, it can still be played, but there is absolutely no sound coming from the game and I have no idea why.

I haven't been able to find anyone suffering any similar issues online. Does anyone have any ideas what's going on, and if so, how do I fix it?

Thanks for reading.

---

### Post by Ladders on 2011-10-22
Never mind. I solved the problem by switching from WINE 1.3 to WINE 1.2.

---

### Post by Mad-Halfling on 2011-10-23
> **Ladders said:**
> Never mind. I solved the problem by switching from WINE 1.3 to WINE 1.2.

I had this and just found a solution.

Just to make sure you've got a newer version of WINE, add the PPA
sudo add-apt-repository ppa:ubuntu-wine/ppa
then run 
sudo apt-get update
sudo apt-get upgrade
and this should get you to WINE 1.3.30+
then edit the ~/.wine/user.reg file, in there find the 
[Software\\Wine\\Drivers]
section (or just search for Drivers) and set 
"Audio"="alsa"
that fixed it for me.  This will set up the driver in the audio tab of winecfg then you can (if necessary, my system was fine with the System Default options) tweak the audio devices

GL&HF
MH

---

