---
title: "how do I add custom launchers in gnome 3?"
date: 2011-12-02
forum: General Help
---

### Post by ausairman on 2011-12-02
I'd like to add custom shortcuts to my unity bar and desktop. I've found lots of sideways, upside down and usually not working hacks in searching for a solution, but figure there must be an "indented" way of adding launchers to the desktop hidden away in gnome 3 somewhere, was hoping someone could point me to it..

---

### Post by efflandt on 2011-12-02
For an app that is able to run directly without options or using a script, you simply run the app, then right click its icon in Unity bar and click "Keep in launcher".  Although, that can sometimes seem temperamental about whether it will take or stick initially (maybe fixed in an update).

I don't think an automatic way to add a custom launcher (script or with parameters) is included with Unity (maybe there is if you also have Classic).  But if you install **alacarte**, you can add a launcher to its menu by running alacarte from an X terminal, and next time you log into X (or relogin) it will be in Dash > Applications where you can drag it to the Unity bar.

Or make a Desktop launcher you can run:```
gnome-desktop-item-edit --create-new ~/Desktop
```I made a Desktop launcher to automate that I called "Make Launcher" that runs (did not seem to work unless quoted and run in sh):```
sh -c 'gnome-desktop-item-edit --create-new ~/Desktop'
```

---

### Post by ausairman on 2011-12-02
Oh right, the "keep in launcher" option works great. However, the link doesn't have an icon (or rather just a question mark). My program has a .xpm icon file, how can I tell unity/gnome to use that?

Also, why is this so complicated? Is it to do with Gnome 3 not being quite ready?

---

