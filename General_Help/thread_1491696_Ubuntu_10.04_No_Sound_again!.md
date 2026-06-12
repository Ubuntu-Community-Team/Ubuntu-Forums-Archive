---
title: "Ubuntu 10.04 No Sound again!"
date: 2010-05-23
forum: General Help
---

### Post by Cubhicbu on 2010-05-23
I have Ubuntu 10.04 on an HP G61 on a 64-bit system. for a long time, i couldn't get the flash to work. then i fixed the flash, and a few days later, the sound quiet working. 

Ubuntu is upsetting me. It seems like when I get one thing fixed, something breaks. >< I just want to uninstall Ubuntu and become a full-time Windows user until I can get a Mac.

---

### Post by Cubhicbu on 2010-05-23
OMFG....the Rythmbox was muted. But that doesn't explain why the login sound is disabled?

---

### Post by fragos on 2010-05-24
When I've sound problem I almost always can fix them by running alsamixer in a terminal window.

---

### Post by epi 1:10,000 on 2010-05-24
I having the same problem.  I have reinstalled 3 separate times and it continues to break after a few days and alsa mixer doesn't fix it.  I also continue to have data corruption, very high memory usage, and network connection issues.  I have had nothing but problems w/ this release while 8.04, 8.10, 9.04, and 9.10 have worked quite well.  I have no idea how to track down all the problems.

---

### Post by fragos on 2010-05-24
I've heard there are problems with Compiz crashing over time. I can't say that Compiz is part of your problem but you might try disabling it. I did to avoid problems. I had a few sound issues with 10.04 but alsa mixer fixed them for me. It seemed that one or more sources got muted by an ap that crashed and the only way to fix them was alsa mixer. Make sure you use left and right arrow to see all the possible adjustments in alsa mixer. There are a lot more sources to adjust than you can get to with the Gnome GUI. My sound is trouble free so I don't have any other suggestions.

---

### Post by booksbuggy on 2011-07-29
Thanks for the suggestion of Installing Alsa Sound Mixer Gui, that fixed my no sound problem. It seemed that somehow the recent updates had completely muted everything in my system and i had to unmute it with the Gui.

---

