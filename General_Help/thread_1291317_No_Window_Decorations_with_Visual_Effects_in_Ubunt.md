---
title: "No Window Decorations with Visual Effects in Ubuntu 9.04"
date: 2009-10-14
forum: General Help
---

### Post by dacox on 2009-10-14
I recently reinstalled Ubuntu 9.04 on an old computer that had been running it. It previously had Visual Effects set to normal and all kinds of ridiculous compiz things like the cube.

I had to enable the proprietary nvidia drivers to turn on visual effects, but now, if I have the visual effects set to anything other than "None" all of the window decorations disappear. I have scoured the web and seen quite a few posts regarding this on older ubuntu versions, and none of the suggested fixes had any positive effect for me (emerald --replace, compiz --replace, editing xorg.xonf, etc).

I am finding this quite frustrating, as I had these things working on the exact same computer, with the exact same version of Ubuntu. Any ideas would be greatly appreciated.

My gfx card is GeForce3 Ti 200 (yes, ancient)

---

### Post by blur xc on 2009-10-14
I'll ask the obvious, simple question- did you manage to accidentally uncheck the window decorations check box in ccsm?  There's a plugin somwhere in there also that lets you toggle window decorations too...  I'm not looking right at it, so I can't say exactly where to look.

BM

---

### Post by dacox on 2009-10-14
Hmm, for some reason ccsm wasn't installed...Anyways, installed it and yes, the window decorations box is checked.
The problem persists, however.

---

### Post by mondeoscotch on 2009-10-16
What do you have in ccsm/windows decoration/command box?
should be '/usr/bin/compiz-decorator'
or
'emerald'
if you got installed one.

---

### Post by oboedad55 on 2009-10-16
You can also install fusion-icon and set your effects that way. I had the same problem once and that fixed it.

---

### Post by ptrinder64 on 2009-11-20
I added ```
emerald --replace
``` into [COLOR="Blue"]**CompizConfigSettingsManager** > **Windows Decoration** > **Command**[/COLOR] on my system when I encountered a similar problem and this seemed to fix it.

---

