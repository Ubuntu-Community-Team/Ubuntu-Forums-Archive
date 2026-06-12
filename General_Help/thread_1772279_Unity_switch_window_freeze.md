---
title: "Unity switch window freeze"
date: 2011-05-31
forum: General Help
---

### Post by ftaylor on 2011-05-31
Hi,

I'm currently running Ubuntu 11.04 with Unity. I have a recurring and irritating problem- sometimes when I switch windows using alt+tab, normally when the window that I have switched to is maximised, the window does not get re-painted until it has been resized. The window doesn't "freeze" as such as it still responds to keyboard and mouse events, but it doesn't appear to respond until it is resized.

Is anyone else having this problem?

Cheers,
Finbarr

---

### Post by Grimpow on 2011-06-01
Yeah, I'm having the same problem here. I THINK the problem is somehow related to ATI graphics. The other computers in my house running natty don't have this issue, only me, and I'm the only one with ATI graphics. The only workaround I have is to keep maximized windows in different workspaces. That seems to prevent the windows from locking up and not "repainting"

---

### Post by k.w.elliott on 2011-06-02
Yea I'm having the same problem as well, and I also have an ATI card.  Separating everything by workspace is fine, but everything randomly stops repainting every once and while.  Hopefully this'll get fixed soon.  I wouldn't have payed an extra $100 for an ATI card if I knew it'd be causing me as much trouble as it has :p

---

### Post by ajinkyaghorpade on 2011-06-21
Same problem here. :( Does anybody have solution for this problem?

---

### Post by ftaylor on 2011-06-21
I managed to fix the problem by changing my application switcher in compiz config settings manager. It seems that the crash is caused by Application Switcher/Static Application Switcher. I changed to Shift Switcher and haven't had a problem since.

---

