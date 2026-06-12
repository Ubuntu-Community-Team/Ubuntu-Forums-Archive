---
title: "audio problem"
date: 2010-05-14
forum: General Help
---

### Post by Drifting Cowboy on 2010-05-14
i just installed kubuntu onto my laptop and for some reason i can pick up the sound when the os loads up and closes but i cant get any audio off anything else. im pretty new to linux so if someone could help me out here or point me in the right direction it would be greatly appreciated. :) thanks

---

### Post by wieman01 on 2010-05-14
First off I would playing around with the mixer and see if sound is simply set to mute. Happens quite regularly.

---

### Post by Drifting Cowboy on 2010-05-14
i checked that already, everything is on.

---

### Post by Drifting Cowboy on 2010-05-14
bump... anybody?

---

### Post by dabl on 2010-05-14
I assume PulseAudio is installed.  If so, you need the pulse volume control:
```

sudo apt-get update && sudo apt-get install pavucontrol paman
```

Alt-F2 "pavucontrol" and take a close look at each "sink" and make sure the tiny mute button is not depressed.  Once it all looks right, open your System Settings > multimedia window and try each "device", using the "Test" button. Change the sequence to put working devices near the top of the list, and the rest at the bottom.

---

