---
title: "Volume sets to max at every boot!"
date: 2009-08-10
forum: General Help
---

### Post by vav on 2009-08-10
Somehow my volume control sets itself to max every time I reboot/turn on the machine! With obvious consequences ](*,):-({|=
What could be wrong? I'm running Jaunty on a dell inspiron 9300 with sigmatel on board audio

---

### Post by kerry_s on 2009-08-10
i add a line in ~/.profile to set my volume at 75% no matter what it was the last time.

**amixer set Master 75% unmute**

---

