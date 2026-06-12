---
title: "Sound from speakers and headphones"
date: 2011-03-14
forum: General Help
---

### Post by DOS Boot on 2011-03-14
I've got a Toshiba laptop which has an issue where sound comes from the speakers and headphones simultaneously. I've tried manually setting up the devices in Sound Preferences but could not find the solution there.

The laptop has a Realtek ALC250 rev 2 chipset which doesn't seem to be listed in the HD-Audio-Models.txt file, but I still tried the method of adding "options snd-hda-intel model=" to the end of the alsa-base.conf file. None of the models listed in HD-Audio-Models.txt have worked so far, though.   

Does anyone have any ideas on how to fix this issue?

---

