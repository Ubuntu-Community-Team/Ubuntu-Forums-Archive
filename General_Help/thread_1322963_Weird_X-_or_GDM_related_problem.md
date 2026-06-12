---
title: "Weird X- or GDM related problem"
date: 2009-11-11
forum: General Help
---

### Post by vanRaewa on 2009-11-11
This has happened two times now, where I observed it myself the second time;
I was using firefox, and suddenly it seemed like the whole screen was frozen, and when I tried to scroll I saw a part of the lower left corner of the screen get updated. The only problem was that it wasn't the "real" lower left corner, it was a copy or perhaps "image" of the lower left corner area placed in in the upper right corner of the screen. 

If I performed an action the on frozen part of the screen, nothing happened there, but the action caused did something in the "copy" instead. For example, if I tried to minimize the Firefox window (in the frozen part of the screen) it was minimized in the "copy". I could even move the window and all. Also, the mouse cursor was drawn and updated on the frozen part of the screen, so it seems that input works as normal given the positions of windows on the frozen part of the screen, but the actual actions occur in the copy.

If I restart GDM, it works again (but I believe this problem will reappear at least once every time). I guess this has something to do with something concerning the X Server (I use a dual screen setup with NVIDIA:s proprietary driver), or perhaps GDM. 

There is one other thing; yesterday I installed Screenlets 0.1.2 and setup a couple of meters (CPU, HDD usage etc.). The problems appeared afterwards, and may be related, but it's just a guess. It could be any number of updates done after installing Screenlets (I usually just update applications when prompted and don't really check what's going to be updated).

Does anyone recognize this? I don't really know where to begin...

---

