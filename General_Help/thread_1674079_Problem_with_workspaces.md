---
title: "Problem with workspaces"
date: 2011-01-23
forum: General Help
---

### Post by Mokolodi1 on 2011-01-23
All of a sudden, my workspaces no longer work the way they are supposed to. For instance, when I drag a window to the side of the screen so that it overlaps with the next workspace, it does not show up in that workspace. Also, the animation for switching workspaces has drastically changed. Could anyone provide any help on what could have caused this change or how to revert it back to how it was before? Thanks in advance for any help!

---

### Post by stinkeye on 2011-01-23
It sounds as though you have reverted to Metacity as your window manager.

Alt+F2
and run 
```
compiz --replace
```


Open Ubuntu Software Centre and search for and install **fusion-icon**

Once installed you will find it in System Tools.

Add it to startup preferences using **fusion-icon** in the command box.

When running it sits in the notification area and has a right click menu
to load the different window mangers.

---

### Post by Mokolodi1 on 2011-01-23
Well, that sure did the trick! I'm just looking though the huge list of options for switching workspaces and windows. Thank you sooooooo much!

---

### Post by Mokolodi1 on 2011-01-23
Well, after installing that add on, I was having a field day changing the options. I seem to have changed an option so that you can't see the top bar which normally has the close, minimize, and maximize buttons. I am utterly confused as to which option would get that bar back on the top of all my windows.

---

### Post by stinkeye on 2011-01-23
Select window decorator > Gtk window decorator


or 
alt+F2 and run
```
gtk-window-decorator --replace
```

---

### Post by Mokolodi1 on 2011-01-23
It says, "No such directory"... Probably not a good sign

---

### Post by stinkeye on 2011-01-23
> **Mokolodi1 said:**
> It says, "No such directory"... Probably not a good sign

**Select window decorator > Gtk window decorator** isn't a command.
It's the menu to select in fusion-icon.

---

### Post by Mokolodi1 on 2011-01-23
Oh, that was silly of me. Still no top bar thing on windows though. It's really annoying actually because you can't close or move anything without keyboard shortcuts.

---

### Post by stinkeye on 2011-01-23
Alt+F2
```
compiz --replace
```



followed by
Alt+F2
```
gtk-window-decorator --replace
```


Some info for you:
Compiz and metacity are both window managers.
While metacity and most window managers will decorate windows with titlebar and borders
without the need for another program,
compiz needs either **gtk-window-decorator** or **emerald** to decorate the window.

---

### Post by Mokolodi1 on 2011-01-23
Still nothing unfortunately

---

### Post by stinkeye on 2011-01-23
> **Mokolodi1 said:**
> Still nothing unfortunately

In fusion-icon make sure in the **compiz options** menu 
that both entries
**loose binding **and
**indirect rendering** are unticked. (you should leave these)

Selecting metacity as your window manager will give you a working desktop without 3d effects.

---

### Post by Mokolodi1 on 2011-01-23
Well, thanks a whole lot for all of your help! I figured it out finally thanks to your explanation :P

---

