---
title: "kde trimmed down?"
date: 2006-03-16
forum: General Help
---

### Post by beforewisdom on 2006-03-16
Until recenltly I was running an OLD ( over a year ) copy of knoppix with the kde.  I remember that all of the config stuff was mostly in a nice neat "control center" including a very friendly keydboard shortcut menu that was customizable.

I installed ubuntu and noticed that the keyboard shortcut menu was limited.

Now that I have a fast connection I decided to check kubuntu out on livecd.  I noticed that control center is now one big window and the really powerful keyboard shortcut config dialog seems to be gone.

Was this a move by the kde or by kubunut( to scale down and make things simple)?

Just curious

Steve

---

### Post by aysiu on 2006-03-16
Try Alt-F2 ```
kcontrol
```

---

### Post by Jucato on 2006-03-16
System Settings is a Kubuntu-only project to be the default. Control Panel for Kubuntu. You can still access KControl, like what aysiu said. You can also add a KControl entry in KMenu (the usual way, through the KDE Menu Editor, kmenuedit). 

Alternatively, you could also do this:
1. Go to the Panel Configuration (either through System Settings, KControl, or right-clicking on the panel)
2. Go to the Menus tab. In the Optional Menus section, enable/check the "Settings" option. This will create a Settings group in K Menu where you can launch KControl itself or only the individual modules inside it.

The keyboard inputs and shortcuts are under the Regional & Accessibility categories in both KControl and System Settings.

---

