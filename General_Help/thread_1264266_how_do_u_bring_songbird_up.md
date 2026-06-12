---
title: "how do u bring songbird up?"
date: 2009-09-12
forum: General Help
---

### Post by Arminius on 2009-09-12
I installed songbird songbird_1.2.0-1~getdeb1_i386.deb, seemed to install fine.
ran songbird in the applications/sound & Video, it seems to execute then vanishes, can't find it anywhere on the display.

I go to run it again and it says no its already running but not responding.
how do I shut it down?

I tried reinstalling with the deb file, but same problem

---

### Post by Tim Sharitt on 2009-09-12
Try to run it from the terminal and post the output (if any) here.

Goto Applications > Accesories > Terminal and enter ```
songbird
``` 
at the prompt.

If you have already tried to run it and you receive a message that it is already running, you can try 
```
killall -9 songbird
```
from the terminal, or just log out and log back in.

---

