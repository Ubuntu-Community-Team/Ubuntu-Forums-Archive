---
title: "Compiz drag program to next workspace?"
date: 2010-04-27
forum: General Help
---

### Post by derande on 2010-04-27
Just installed most recent 64-bit Lucid RC last night and after fiddling around through Compiz, I cannot figure out how to drag an open program over to the next desktop workspace.
I use 4-workspaces (4x1) and while running 9.10, I could grab the title bar of an open program and drag it from workspace 1 to 2 or 3.
Now I can right click the title bar then move to another workspace or drag the program halfway into the next work space '2', then click over to workspace '2' and complete the move. But I would like to be able to completely drag it over again.
How is this accomplished?

Thank you in advance!

---

### Post by stinkeye on 2010-04-27
You need these settings in 
CCSM > Desktop > Rotate Cube

---

### Post by derande on 2010-04-27
thanks, that definitely works now but previously i didn't use desktop cube; i could just drag from one workspace to another.

i can use it this way but the cube makes me ***dizzy***.

---

### Post by antenna on 2010-04-27
Then Desktop Wall is what you want.  The drag options are in the Edge Flipping part.

---

### Post by derande on 2010-04-27
> **antenna said:**
> Then Desktop Wall is what you want.  The drag options are in the Edge Flipping part.

that's it!
thanks to both of you!

---

### Post by Matt G Dalian on 2010-05-09
I had the same problem- after upgrading to Ubuntu 10.04 Lucid Lynx I was no longer able to drag windows over to a new virtual desktop.

For whatever reason, after upgrading (from 9.10 Karmic) the setting "Edge Flip Move" was unchecked. So I just had to re-check it.

It's under System -> Preferences -> CompizConfig Settings Manager
Then choose Desktop Wall
Last tab (Edge Flipping)


(maybe more specific than the conversation above)

---

