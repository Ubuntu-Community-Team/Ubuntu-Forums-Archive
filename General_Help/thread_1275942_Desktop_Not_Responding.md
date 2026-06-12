---
title: "Desktop Not Responding"
date: 2009-09-26
forum: General Help
---

### Post by Brandma on 2009-09-26
I'm having a really strange problem.  No icons appear on the desktop at all, but when I go to the desktop folder, everything is there.  Also, I am unable to highlight portions of the desktop or right click it, but clicking it and moving enables compiz's desktop cube still.  Any ideas?

---

### Post by fela on 2009-09-26
```
ps -ax | grep nautilus
```

Run that when you've just logged in. If there isn't any 'nautilus' process apart from the 'grep nautilus' thingamebob, something's wrong.

---

### Post by Brandma on 2009-09-26
Thanks, yeah it was just Nautilus.  In my attempts at restarting/logging off and back on, Nautilus doesn't autostart.  How do I edit that?

---

### Post by fela on 2009-09-26
> **Brandma said:**
> Thanks, yeah it was just Nautilus.  In my attempts at restarting/logging off and back on, Nautilus doesn't autostart.  How do I edit that?

Go to system > preferences > startup applications (could be sessions) and add an item, with command 'nautilus'. That's it - should be anyway :).

---

### Post by Brandma on 2009-09-26
Got it, thanks!

---

