---
title: "No sound with 64-bit Flash"
date: 2011-09-16
forum: General Help
---

### Post by DemonSharkKisame on 2011-09-16
I found time this morning to do a clean reinstall of Ubuntu, and decided to go with Kubuntu 64-bit. So far, everything seems to work... everything, that is, except sound in Flash. I installed Flash through the sevencomputers PPA as it had the 64-bit installer, but oddly, there's no sound coming through my headset. I can hear everything else just fine, so why not Flash? Am I missing something? :confused:

---

### Post by Lisiano on 2011-09-16
I just installed Flash 64-bit from ppa:sevenmachines/flash and it seems to work normally. Hearing that you installed Kubuntu I have a feeling it might be related to something I had a few days ago. Try going into System Settings -> Multimedia -> Phonon and find a device that you can hear (I have some weird device that outputs somewhere but I can't find where.. Yet) and move it to the top of the list then apply the device list to everything

---

### Post by DemonSharkKisame on 2011-09-16
Thanks, but I got sound working with Flash. Turns out that regular Flash in the default Ubuntu repos works fine, for some reason. Now the only real issue I have is getting my USB headset to work properly with Skype (I can hear the other end, but they can't hear me), but I don't think Ubuntu Forums is the best place for Skype help. >_>;

---

### Post by Lisiano on 2011-09-16
I'm guessing you can't pick what input to use in Skype. Same stuff in phonon except with the Audio Capture. Or if you don't mind installing GTK, you could install padevchooser, pavucontrol and pavumeter to set the default input.

PS. The normal flash (32-bit actually) always worked for me (I always used 64-bit OS installs on this machine)

Also since the original problem is solved. Please mark the thread as solved in the Thread Tools above.

---

