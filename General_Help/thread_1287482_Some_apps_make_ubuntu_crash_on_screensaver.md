---
title: "Some apps make ubuntu crash on screensaver"
date: 2009-10-10
forum: General Help
---

### Post by jolindbe on 2009-10-10
When some applications are running (Matlab and OpenOffice are the ones I've noticed doing this), and the screensaver starts, the computer will sometimes crash.

Or, crash is perhaps not the best word - when I move the mouse, the screensaver will vanish slowly, first from the upper parts of the screen, then running downwards (I hope you get what I mean). I can still use the computer, but everything updates extremely slowly - when I write something, or change window, or clicks on a menu, the screen updates the same way - slowly from the top to the bottom in maybe 3 seconds for the full screen to load.

The only help seems to be reboot. Anyone who has met the same?

I am using Intrepid on a Dell Latitude D830, with Nvidia graphics.

---

### Post by XCan on 2009-10-10
Does this happen with all screensavers? What happens if you only use the 'blank screen' variant?

---

### Post by jolindbe on 2009-10-11
I think that it usually happens first when the screen has gone blank (power save, or whatever it is called). However, my power settings are that the screen never should power off while on external power source, but I'm quite sure it does...

---

### Post by lavinog on 2009-10-11
Your system might not have enough memory, or the screensaver leaking memory.

use **free -m** to report your memory usage before and after the screensaver starts.

---

### Post by jolindbe on 2009-10-13
Also happens when screen saver is selected to blank screen.

I tried to get into the terminal after the computer froze last time, but nothing happens when I try to enter commands.

Or did you mean that you wanted to see the result before and after the screen saver starts if I stop the screensaver before it starts freezing? Because it normally takes some time for the screensaver to crash the 'puter.

---

### Post by lavinog on 2009-10-13
> **jolindbe said:**
> Also happens when screen saver is selected to blank screen.
That should rule out 3d issues.

> 
Or did you mean that you wanted to see the result before and after the screen saver starts if I stop the screensaver before it starts freezing? Because it normally takes some time for the screensaver to crash the 'puter.
yes

---

### Post by jolindbe on 2009-10-15
Ok, the free -m returns this before screen saver:

```
             total       used       free     shared    buffers     cached
Mem:          2022       1620        402          0        238        751
-/+ buffers/cache:        630       1391
Swap:         2353          6       2347

```

and this after screen saver running for about an hour without crashing (and without the heavy programs running):

```
             total       used       free     shared    buffers     cached
Mem:          2022       1660        362          0        240        765
-/+ buffers/cache:        654       1368
Swap:         2353          6       2347

```

Edit: By the way, thanks for your time and help!

---

### Post by lavinog on 2009-10-15
does it crash if the screen saver is disabled, and the screen is set to turn off?

---

