---
title: "All panels have disappeared after computer froze"
date: 2010-11-15
forum: General Help
---

### Post by Feite on 2010-11-15
Hi, 
I'm pretty new to Ubuntu, and I'm currently running it as a dual-boot together with Windows 7. I hadn't had any problems up till yesterday, when all of a sudden Ubuntu stopped responding (I wasn't doing anything special, running firefox and mathematica) while opening a new tab (youtube). I waited for a few minutes, still no response, and then hard booted it. When starting it up again, all my panels had disappeared.. The pictograms on my desktop are also moving up and down about a pixel continuously about once a second. I'm still able to run a terminal using shortcuts, and thus launch any program, but I have no idea how to recover the panels, and am still wondering how to prevent them from disappearing. I can make a screenshot on request, but there is really nothing to see except for a few pictograms. I am also using two monitors and 10.10 if that is of any importance. Does anyone know what the issue might be or how to resolve it?

---

### Post by mister_playboy on 2010-11-15
Are your monitors showing the same desktop or different ones?  If you're booting into a mirrored monitor mode or booting with only one of the two screens turned on, your panels may be currently on the invisible desktop.

You can run the monitor program from the command line with ```
gnome-display-properties
```

---

