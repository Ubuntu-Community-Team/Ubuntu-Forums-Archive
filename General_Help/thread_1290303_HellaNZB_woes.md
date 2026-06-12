---
title: "HellaNZB woes"
date: 2009-10-13
forum: General Help
---

### Post by ManCrab on 2009-10-13
I've been using hellanzb_0.13-3 from the repositories on my Hardy box for a while, but now experience irregular software behavior.

#1 - If I download an NZB that contains another NZB, hellanzb will hang before par2verify/repair and unraring.
At this point the program has to be stopped, files copied, and par2repair done manually if recovery is needed.  

#2 - When a queued download finishes, hellanzb is skipping the unrar step, This isn't constant but is happening more 
and more frequently.  Has anybody experienced this? Is there a fix? This is/was one of the programs I use most frequently.

---

### Post by Intrepid Ibex on 2009-10-13
This probably won't help you at all, but switching to Jaunty (or upcoming Karmic) will fix issues.. even though it will also come with some new issues.

Either way at least you will get newer software, as with Ubuntu most packages "lock" their versions, in which case hardy still has e.g. firefox 2 (or maybe 3) and openoffice 2.4.

Some bugfixes and major security updates is still being applied though :/.

---

### Post by sddfdds on 2009-10-26
Karmic/Jaunty have the same version of hellanzb, and they have the problem too...i think it's something python related because hellanzb hasnt changed significantly in ubuntu for a while

---

