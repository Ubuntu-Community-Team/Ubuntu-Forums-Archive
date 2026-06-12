---
title: "Unity2D Launcher Toggle"
date: 2011-10-27
forum: General Help
---

### Post by KoopaTroopa on 2011-10-27
So at times when I'm switching from window to window regularly it would pay to have the unity launcher set to 'always show'. So not as to painstakingly move the cursor all the way over to the left, wait for the launcher to appear, then find the window I want to move to.

But other times I may just be browsing the web for some time and not needing to switch from window to window. In which case it would be nice to have the launcher to 'dodge windows'. 

So to solve this I would simply need to assign a hotkey that would check if the Unity2D launcher was set to 'always hide' if so then change it to 'dodge windows' and visa versa. But unfortunately I don't know how to change the launchers settings via terminal command. I did find on askubuntu.com the same question but the commands provided did not change the launchers settings. Does anyone know how I can do this?

Thankzies!

---

### Post by KoopaTroopa on 2011-10-28
_Bump_er cars.

---

### Post by Vaphell on 2011-10-28
have you considered using fullscreen mode in firefox? (f11)

either way try writing a script that switches between

```
dconf write /com/canonical/unity-2d/launcher/use-strut true
dconf write /com/canonical/unity-2d/launcher/hide-mode 0

```

and
```
dconf write /com/canonical/unity-2d/launcher/use-strut false
dconf write /com/canonical/unity-2d/launcher/hide-mode 2

```
and set up hotkey for it

use-strut makes launcher space not available to windows while hide-mode defines behavior of the launcher. i think 0 is always on, 1 is auto-hide, 2 is dodge. Play with combinations if it's not exactly what you want

i noticed in my experiments that when you switch from 1 to 0 the already hidden launcher is completely disabled and can be only shown with WIN key. It looks like a bug but can be useful to people who want to use some standalone dock app.

goto keyboard prefs, create a new shortcut, eg ctrl+space and paste this
```
sh -c 'if [ $(dconf read /com/canonical/unity-2d/launcher/use-strut) = true ]; then dconf write /com/canonical/unity-2d/launcher/use-strut false; dconf write /com/canonical/unity-2d/launcher/hide-mode 2; else dconf write /com/canonical/unity-2d/launcher/use-strut true; dconf write /com/canonical/unity-2d/launcher/hide-mode 0; fi'
```

---

