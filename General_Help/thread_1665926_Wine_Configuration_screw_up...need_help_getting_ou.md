---
title: "Wine Configuration screw up...need help getting outta this mess"
date: 2011-01-13
forum: General Help
---

### Post by Dangerzone812 on 2011-01-13
Ok, so I was playing around on the graphics tab....and I saw the screen resolution slider, and I slid it up thinking that it would help it look better. Now I'm stuck with only being able to see what's below on my screen, and now I don't know how to bring it down again. HELP!

---

### Post by Verbeck on 2011-01-13
try renaming the *.wine *folder in your home folder to *.wine-backup*
(press ctrl+H to see hidden folders)

---

### Post by Dangerzone812 on 2011-01-13
Ok, I did it, and I could see it, now do I just change it back?

---

### Post by micha8l on 2011-01-13
Looks like you'll need to manually edit winecfg, see here: [http://www.linuxforums.org/forum/wine/55611-manually-editing-winecfg.html](http://www.linuxforums.org/forum/wine/55611-manually-editing-winecfg.html)

---

### Post by Verbeck on 2011-01-13
> **Dangerzone812 said:**
> Ok, I did it, and I could see it, now do I just change it back?
open 'configure wine' and a new profile would be created, then just delete the .wine-backup folder if everything works fine(copy over the 'drive_c' within to the new profile if you have any wine apps installed)

---

### Post by Dangerzone812 on 2011-01-13
Perfect! 

Solved!

---

