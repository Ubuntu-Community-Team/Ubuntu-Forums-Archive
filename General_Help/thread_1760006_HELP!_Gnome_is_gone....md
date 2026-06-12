---
title: "HELP! Gnome is gone..."
date: 2011-05-16
forum: General Help
---

### Post by galacticaboy on 2011-05-16
I have Ubuntu 11.04 and Gnome is now gone. I have tried everything, I can login and see my desktop but my panels are not there, I cannot do alt+f2 nothing happens, I cannot bring up a terminal, I can only get on Firefox by right clicking on the desktop and clicking change desktop background, then I click on the "get more backgrounds online" and that will bring up firefox, I cannot get anything else to open, I have restarted. When I do CTRL+ALT+F2 to bring up the console and login there, I do "startx" command and nothing happens... what do I do??? Please help!
David

---

### Post by Grenage on 2011-05-16
When you are at the login screen, do you got the choice of Desktop Environments to log into, or are you using Unity as is default?

From a terminal, what does this do for you:

```
unity --reset
```

---

### Post by galacticaboy on 2011-05-16
I cannot use Unity, my graphics card cant do it, so I have been using Gnome Classic, and not when I login to Gnome Classic my panels are not there and I cannot open a terminal or anything...

---

### Post by galacticaboy on 2011-05-16
I got it, somehow my Gnome-Panel was uninstalled, I must have accidentally done it when I uninstalled the Unity 2D Desktop that I had... thanks for the help though!

---

### Post by Grenage on 2011-05-16
Ctrl-Alt-T 'should' give you a terminal.

Then try:

```
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by Grenage on 2011-05-16
> **galacticaboy said:**
> I got it, somehow my Gnome-Panel was uninstalled, I must have accidentally done it when I uninstalled the Unity 2D Desktop that I had... thanks for the help though!

Lol, that would do it; glad it's sorted.

---

