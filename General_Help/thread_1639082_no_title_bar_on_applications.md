---
title: "no title bar on applications"
date: 2010-12-06
forum: General Help
---

### Post by evanston4393 on 2010-12-06
More than half of the time when i boot up, all windows that i open are without a title bar (this includes the close, maximize, and minimize buttons). Does anyone have any idea why this is happening? I've included a picture of what is happening

---

### Post by searchfgold6789 on 2010-12-06
Try changing your window manager style.

---

### Post by sikander3786 on 2010-12-06
Press Alt + F2 and reload Window Manger by either,

```
metacity --replace
```

Or if using compiz,

```
compiz --replace
```

Or see this.

[http://ubuntuforums.org/showpost.php?p=9997848&postcount=2](http://ubuntuforums.org/showpost.php?p=9997848&postcount=2)

---

### Post by WorMzy on 2010-12-06
You could try adding an entry for metacity in your startup applications list (System -> Preferences -> Startup Applications), although if metacity is crashing (and not merely failing to launch), then this won't have any effect. So make sure that metacity still works first by opening a terminal and running "metacity".

EDIT: I just noticed that your panels are missing too. Is this intentional, or is gnome-panel failing to launch too?

---

### Post by evanston4393 on 2010-12-06
[QUOTE=]
EDIT: I just noticed that your panels are missing too. Is this intentional, or is gnome-panel failing to launch too?[/QUOTE]

When i took the screenshot i only included the window, the panels are working fine. 

Thank you for the suggestion of restarting Compiz, next time the issue occurs i will try that.
Does anyone have any idea of why Compiz is crashing? This did not used to happen.

---

