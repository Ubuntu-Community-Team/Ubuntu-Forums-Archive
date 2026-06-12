---
title: "AMD Driver (fglrx, Catalyst 11.3) Identify Displays won't go away"
date: 2011-04-07
forum: General Help
---

### Post by cfalzone on 2011-04-07
Hi all,

I installed the AMD Catalyst 11.3 package and I'm noticing that whenever I play a game (so that the monitor changes resolutions) the little red display identifier pops up. You can see what I'm talking about in the AMDCCC in the Display Manager section by clicking the finder (magnifying glass) button.

This is frustrating as it sits directly in the middle of the games I want to play. Is there a way to disable display identifiers? I don't need to know that my laptop LCD is different display than my Asus monitor... I can already see the device names.

Sorry if my description isn't ample, but I cannot screenshot it because it will not be included in the shot...

Thanks for any ideas!

---

### Post by unimatrix on 2011-04-10
Same problem. The only way to go rid of it is to go into Catalyst Control Center and untoggle "Identify Display" under "Display Manager".
It's still very annoying, because some Wine or DOSBox games change the resolution and the damn thing reappears.

EDIT: Nevermind, found a solution: [http://forum.sabayon.org/viewtopic.php?t=23135](http://forum.sabayon.org/viewtopic.php?t=23135)
I had to comment out the "*Viewport   0 0*" line out of my /etc/X11/xorg.conf

---

### Post by cfalzone on 2011-04-10
Somehow the issue resolved itself on my system. Though I did nothing to bring about the change (not even restart).

---

### Post by jjinco33 on 2011-07-14
Gah. After a reboot the other day this began happening again for me. Every time I play a full screen game and the resolution changes the box comes back and sits over my game window in the corner, and once in the middle of the screen.

This worked for me...
EDIT: Nevermind, found a solution: [http://forum.sabayon.org/viewtopic.php?t=23135](http://forum.sabayon.org/viewtopic.php?t=23135)
I had to comment out the "*Viewport   0 0*" line out of my /etc/X11/xorg.conf

---

