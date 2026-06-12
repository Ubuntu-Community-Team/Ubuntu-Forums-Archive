---
title: "Application bar missing globally"
date: 2011-08-03
forum: General Help
---

### Post by DJ_Tripcode on 2011-08-03
Hey all,

The menu bar located at the top of application windows is missing from all open applications, even if the application specifies that the menu bar is visible. I have not attempted to reproduce in another WM.

Printscreen: [http://i.imgur.com/XC7S7.png](http://i.imgur.com/XC7S7.png)

Anybody have any ideas?

---

### Post by dj722000 on 2011-08-03
LOL how ironic, I just fixed mine.

System / Preferences /  CompizConfig Settings Manager / Effects / Window Decoration

It takes a few seconds for it to come on, so don't panic.

---

### Post by Jose Catre-Vandis on 2011-08-03
That's fine for Ubuntu but things are slightly different in Xubuntu with xfce. (assuming the OP is not running compiz ;))

Try running this command in your terminal:

```
xfwm4
``` (you may need sudo)

Hopefully your menu bar will return. To ensure it is there next time you login, go to Settings > Session and Startup > Session and Click on Save Session.

---

### Post by DJ_Tripcode on 2011-08-04
Starting the window manager manually did not resolve the issue.

However, I logged into a GNOME session and replaced the GNOME WM the Xfce window manager. That resolved the problem.

Any thoughts?

---

### Post by Toz on 2011-08-04
It really looks like the xfwm4 window manager wasn't working (crashed). Log back into xfce and try instead, the command:
```
xfwm4 --display=:0.0 --replace
```

What do you mean by "replaced the gnome WM with the xfce window manager"? What command did you run?

---

