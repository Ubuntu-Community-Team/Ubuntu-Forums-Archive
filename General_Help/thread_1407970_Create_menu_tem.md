---
title: "Create menu tem"
date: 2010-02-15
forum: General Help
---

### Post by Jpenguin on 2010-02-15
I have a few item I want to add menu items for that require me to 'cd' to a directory first.

In terminal, I can enter "cd '/home/jpenguin/.wine/dosdevices/c:/Program Files/racer065' ; wine ./racer.exe"

It's easy to make a menu item like this in KDE, but I want to use gnome.  How?

---

### Post by jamesisin on 2010-02-15
If you want to make an application launcher on a panel, it is easy to create a custom one.

Right-click on an empty spot in the panel in question and choose "Add to Panel..." from the menu which appears.

Choose Custom Application Launcher on the Add to Panel dialog (it should be the first in a long list of choices).

In Command you want:

```
env WINEPREFIX="/home/jpenguin/.wine" wine "C:\Program Files\racer065/racer.exe"
```

Fill in the other two fields to your liking.

(I didn't test this, but it ought to work.)

---

