---
title: "failed installation - blank screen of death"
date: 2006-03-23
forum: General Help
---

### Post by unclben on 2006-03-23
I tried to install Breezy on an old Dell L700cx with a TNT2 videocard. The installation went smoothly, but at the point when the installer usually finishes up and loads gdm, my screen just goes blank. When I restart, I go from usplash to the blank screen. I've tried it twice, with identical results.

The screen is totally black except for a text cursor (i.e. a white underline) in the top left corner. The system appears to be totally locked up. I can't Ctrl+Alt+Backspace, Ctrl+Alt+Del, Ctrl+Alt+F1, or anything.
:confused:

---

### Post by John.Michael.Kane on 2006-03-23
Try reinstalling using this command linux noacpi this may help

---

### Post by unclben on 2006-03-23
Update:

Based on some Googling, I tried booting with a different monitor: no luck there. Afterwards, I was fiddling around in the BIOS when I realized that the Dell has onboard video! I enabled that, and rebooted. It did the 'blank screen of death' thing for about 10 seconds, then gdm came up! I got real excited, after another 10 seconds the 'blank screen of death' returned. Another 10 seconds went by, and then an ncurses screen came up - it looked straight out of the Breezy installer.

The top-left corner read 'Ubuntu Configuration' and Ubuntu was downloading packages like mad (144 of them). The packages seemed pretty random, but were strongly biased towards KDE (which is odd, since I installed regular ol' Gnomerific Ubuntu). The packages installed themselves, gdm restarted, and I was greeted with the Edubuntu logo! I logged in, and everything seems to be working okay.

Does anybody have any idea what in the heck is going on? Does Ubuntu have some way to say 'Oh, good lord this guy's computer sucks. He must be a little kid on a hand-me-down computer, so I'll install Edubuntu, which also happens to support some craptacular video hardware that Ubuntu doesn't!'?

---

