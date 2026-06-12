---
title: "Microphone not working"
date: 2010-03-04
forum: General Help
---

### Post by Compintuit on 2010-03-04
Hello all, I've got a new laptop, and after testing to make sure everything was working on windows I installed ubuntu. Only problem is, the internal microphone doesn't seem to work. I can't get it to record anything, and I don't see it anywhere. Does anyone have any ideas how to test if it is even being detected, and how to get it working? Thanks

EDIT: I've managed to make the microphone work, after extensive testing of various config options. None of that actually made it work; what you want to do to make it work is install the package linux-backports-modules-alsa-karmic-generic, then it will just work. Computer model is an acer Aspire 4810TZ.

---

### Post by Greenwidth on 2010-03-04
If you right click the speaker icon > Sound Preferences the microphone settings should be on the input tab. 
You might also need to set it to 'Duplex' (ie in and out) on the hardware tab.

---

