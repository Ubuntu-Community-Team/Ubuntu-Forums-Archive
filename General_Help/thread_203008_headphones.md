---
title: "headphones"
date: 2006-06-24
forum: General Help
---

### Post by GreatestGravity on 2006-06-24
So, I've recently had this strange problem - my headphones stopped working! Internal laptop speakers still work, but when I plug in headphones I get no sound from either headphones or speakers.

Problem wasn't triggered by any sort of upgrade, I don't think - it might have been caused by one period where my laptop was interrupted when booting up from hibernation followed by another interrupted bootup, but I'm really not sure, it could've been caused by something else. 

Since then I've done the upgrade to the latest kernel version that was suggested by the upgrade manager, that didn't change anything.

Does anyone have ideas for what it could be or how I could fix it, or at least where to start looking?

---

### Post by GreatestGravity on 2006-06-25
So, I looked around a bit more, and happened across one place that did help - my settings in alsamixer were messed up. 

So if anyone else has trouble with these things, try running "alsamixer", unmute and turn on everything, see whether that helps. (Save settings with alsactl store)

---

