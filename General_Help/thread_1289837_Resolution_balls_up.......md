---
title: "Resolution balls up......"
date: 2009-10-12
forum: General Help
---

### Post by Jedwinjim on 2009-10-12
Hi, after recently installing ubuntu untrepid on my desktop computer, and updating all the packages, and importing all my music, and downloading all codecs needed (and getting everything else up to scratch after many hours) I was fooling around with visual stuff when I changed my screen resolution..... disaster. My screen is now completely borked. Funnily the screen is fine when asking for my username, followed by password... although on loadup the screen goes completely mental & becomes completely unusable. I'm confident all I need to do is change the resolution back to how it was.... but how can I do this if I don't have a screen to look at to do it?

All help MUCH appreciated,

regards,

Joseph.

---

### Post by PrePenguin on 2009-10-12
I found out real quick if you change the bits in the startup manager it will ruin the resolution on the splash screen and spook the system from that point on only fix i found was re-installing, not sure if this is what you did but its very sensitive to graphical interfacing.

---

### Post by wojox on 2009-10-12
Press Esc key and boot into single user mode and a root shell. Then reset X:

```
dpkg-reconfigure -phigh xserver-xorg
```

Then:

```
reboot
```

---

