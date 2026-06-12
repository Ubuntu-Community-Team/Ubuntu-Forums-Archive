---
title: "Unity Launcher woes..."
date: 2012-01-15
forum: General Help
---

### Post by jpin321 on 2012-01-15
Ok so I'm running Ubuntu 11.10 x64 im not a huge fan of Unity but I'm getting used to it.  I've just recently developed a problem I can't resolve and my google foo isn't turning over any new rocks for me.

My launcher is set to "dodge windows" it does this well except for one problem.  If I have a window too close to it or a maximised app it will not show itself when i mouse over to the edge of the screen.  I have to move the window or minimise the app to make it visible again.  I was initially annoyed that it was too sensitive and was always in the way of the back button on my browser.  Now I kinda miss it working :)  Any help would be appreciated.

---

### Post by MG&amp;TL on 2012-01-15
How did you set it?

Install compizconfig settings manager, then click on the Unity button, then change to something else and back again, see if that fixes.

---

### Post by jpin321 on 2012-01-15
> **MG&TL said:**
> How did you set it?

Install compizconfig settings manager, then click on the Unity button, then change to something else and back again, see if that fixes.

Tried that set it to auto then back to window dodge.  Still the same issue.  I know I probably changed something that broke it but I can't figure out what. ](*,)

---

### Post by MG&amp;TL on 2012-01-15
Well, you can run:

```
unity --reset
```

which completely resets Unity, or you can click all of the little cross signs on the right hand side of CCSM to reset to defaults.

---

### Post by jpin321 on 2012-01-15
I figured it out finnaly.  I enabled desktop cube when I did it set reaveal mode to none. /shrug. I'm not sure why but I set it back to the left side now all is well.  Thanks for your help, hopefully this will help someone else.

---

