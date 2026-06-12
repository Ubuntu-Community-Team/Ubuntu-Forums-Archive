---
title: "Inconsolata fonts get cut off in terminal"
date: 2010-02-17
forum: General Help
---

### Post by Mustache Villain on 2010-02-17
The Inconsolata font gets cut off in terminal for some strange reason. The rest of the other font faces are fine. It's only an issue with this font. I attached a screenshot.

---

### Post by bgbraithwaite on 2010-08-17
I have the exact same problem, I've been trying to hunt down the solution for a while now, because I really like Inconsolata. Right now I'm having to live with my old standby Courier New :( .

---

### Post by bgbraithwaite on 2010-09-07
[https://bugs.kde.org/show_bug.cgi?id=226308](https://bugs.kde.org/show_bug.cgi?id=226308)

It seems that this is not a problem just with Inconsolata, but is a bug in the way Qt (or at least Konsole and Kate) renders bold fonts. At least for one guy, updating to KDE 4.5 SC fixed it :) . For me, my adventures in updating to 4.5 didn't seem to have an effect on this particular bug, but it may be worth a try.

---

