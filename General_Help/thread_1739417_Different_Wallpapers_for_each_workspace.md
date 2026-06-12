---
title: "Different Wallpapers for each workspace?"
date: 2011-04-25
forum: General Help
---

### Post by El3mentGamer on 2011-04-25
Im running Ubuntu 10.10 is this possible?
Is it possible to set a different wallpaper for each workspace?

---

### Post by Krytarik on 2011-04-25
You can try Compiz' "Wallpaper" plugin for that, apparently the only way currently. Therefore you need to install the package "compiz-fusion-plugins-extra", it's in the official repos.

But this implies the loss of the usual desktop features, like items on it, you may need to disable Nautilus' handling of the desktop manually, if it's not done by the plugin automatically, therefore disable the key "/apps/nautilus/preferences/show_desktop" in "gconf-editor".

Also, you may need to switch to a console and back to your xsession each time you log in, for example with Ctrl+Alt+F1 and Ctrl+Alt+F7/F8, to make the plugin apply the chosen background images.

Greetings.

---

