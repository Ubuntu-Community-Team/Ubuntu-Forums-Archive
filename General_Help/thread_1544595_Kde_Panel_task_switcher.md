---
title: "Kde Panel task switcher"
date: 2010-08-02
forum: General Help
---

### Post by SirPecanGum on 2010-08-02
I have accidentally deleted the Panel in KDE. What is the window / task switcher called and how do I add it to the panel, please?

---

### Post by TheNerdAL on 2010-08-02
You could try this if you mean the panel at the bottom: 

> **Zorael said:**
> Well, you could delete the settings file and have it recreate itself.
```
$ kquitapp plasma-desktop
$ rm ~/.kde/share/config/plasma-desktop-appletsrc
$ plasma-desktop &>/dev/null
```
Or, in one line for easy copy/pasting;
```
kquitapp plasma-desktop; rm ~/.kde/share/config/plasma-desktop-appletsrc; plasma-desktop &>/dev/null
```
Just paste that in a terminal.

edit: As a sidenote, they're adding templates in future versions of Plasma. With those you could just add a Default Panel and it'd look as it did at first login.

---

### Post by SirPecanGum on 2010-08-02
Thanks for your prompt reply but if I wanted to type commands in a console I wouldn't be using a GUI. Thanks anyway.

---

### Post by SirPecanGum on 2010-08-02
It is called Task Manager but it is difficult to find due to the amount of stuff clogging up the add widgets dialogue. Requesting Add Widgets twice reveals a search box which helped to solve the problem. Almost certainly my fault entirely as I don't give enough time to playing with widgets.

Nothing helps me to appreciate Windows as much as KDE does...

---

