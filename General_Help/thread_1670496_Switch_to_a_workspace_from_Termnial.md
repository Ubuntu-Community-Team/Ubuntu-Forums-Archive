---
title: "Switch to a workspace from Termnial"
date: 2011-01-19
forum: General Help
---

### Post by winchendonsprings on 2011-01-19
Can someone tell me how to switch to a workspace from the terminal?

This may seem incredibly silly and may last less than a day in my virtualbox I use for web development, but I want to create a couple Desktop "launchers" to specific workspaces that I can resize the icon big on the desktop.

---

### Post by dcstar on 2011-01-19
> **winchendonsprings said:**
> Can someone tell me how to switch to a workspace from the terminal?

This may seem incredibly silly and may last less than a day in my virtualbox I use for web development, but I want to create a couple Desktop "launchers" to specific workspaces that I can resize the icon big on the desktop.

```
man wmctrl
```

---

### Post by dcstar on 2011-01-19
> **winchendonsprings said:**
> Can someone tell me how to switch to a workspace from the terminal?

This may seem incredibly silly and may last less than a day in my virtualbox I use for web development, but I want to create a couple Desktop "launchers" to specific workspaces that I can resize the icon big on the desktop.

```
man wmctrl
```

---

### Post by winchendonsprings on 2011-01-19
Can't do it without installing something? I saw wmctrl while searching but it seems like such a simple task I shouldn't need to install something.

---

### Post by winchendonsprings on 2011-01-19
essentially the same as this -

[http://www.uluga.ubuntuforums.org/showthread.php?t=623867](http://www.uluga.ubuntuforums.org/showthread.php?t=623867)

---

### Post by stinkeye on 2011-01-19
If using metacity.
Install wmctrl and create a script
```
#!/bin/bash

wmctrl -s [COLOR="Magenta"]desktop number[/COLOR]
```

Desktop numbering starts at zero.


or for compiz.
Install xdotool and use the viewport switcher plugin in ccsm to bind keys to switch to certain desktops.
eg
```
#!/bin/bash

xdotool key super+1
```

---

