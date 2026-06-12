---
title: "Date and Time Help Needed"
date: 2009-10-13
forum: General Help
---

### Post by nvikram on 2009-10-13
Alright, so here's the problem. Over the years of trying ubuntu out, never thought that I would have this problem but, here it is. At the time of this post it is 9:10pm PST. My clock applet states that it is 4:10am PST. So, I right click on the applet (gnome-panel) and hit time settings. Guess what, the system time is 21:10 (i.e. 9:10pm). So, why is it not showing up on gnome-panel? Please help. (BTW, this is ubuntu 9.10 beta)

Thanks for everything. :)

---

### Post by easoukenka on 2009-10-13
That sounds like an annoying problem :)

Take a look at terminal command time see what that says.  Try removing and adding the applet see if that works at all.  Rename the .gnome folder and restart X to restore original settings see if you still experience the problem.

If nothing worked  I would look for an alternative clock applet and make a bug report.

---

### Post by nvikram on 2009-10-13
Thanks, removing and re-adding solved the issue :D

---

