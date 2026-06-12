---
title: "What is this error :D ?"
date: 2010-10-31
forum: General Help
---

### Post by SuperUserDO on 2010-10-31
when i press alt+ctrl+f1  to lunch terminal i get this screen.
Is this error with my mobo chipset (ati radeon xpress 1250):confused:
what can i do to solve it?

---

### Post by jjpcexpert on 2010-10-31
Your computer is being far too verbose. Ignore them. They are not part of stdin or stdout, they are on stderr. :oops: to you.

---

### Post by JKyleOKC on 2010-10-31
Those errors come from the bootup process, which starts on TTY1; they indicate that your monitor, like many, is sending an invalid EDID block back to the system as part of its initialization. The EDID block tells the X server all about the monitor's requirements, but today's X servers are far more picky about the response than they were 5 to 10 years ago -- and many monitor manufacturers fail to provide the block in a format that today's servers expect. If your GUI seems to be working properly you can ignore these errors; if not, search the forums for threads about "black screen" conditions. There are lots of them!

Try using ctrl-alt-F2 instead of F1, and you ought to get a more normal login on TTY2 rather than TTY1. Or, as the other post says, just ignore them and enter your User Name as if they were not there.

---

### Post by SuperUserDO on 2010-11-01
Thank you guys.
Thanks JKyleOKC for your detailed answer i think i will just ignore this error because every thing is working properly :D

---

