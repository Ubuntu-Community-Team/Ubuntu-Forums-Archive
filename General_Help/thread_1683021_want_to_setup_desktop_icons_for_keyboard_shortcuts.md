---
title: "want to setup desktop icons for keyboard shortcuts yet unsure how"
date: 2011-02-06
forum: General Help
---

### Post by hart02 on 2011-02-06
I know about hotkeys and setting up keyboards shortcuts.But say I had no keyboard like say a tablet.I have an s10-3t and I got compiz on it. I would like to be able to create shortcut icons for executing keyboard commands for use with compiz. All I would have to do is click the icon and it would execute. I would not have to remember all the keyboard shortcut commands I setup. I could also impress people I meet with it far easier. Anyone's help would be great.

---

### Post by Krytarik on 2011-02-06
You could use "xdotool" for that, it's in the official repos:
```
sudo apt-get install xdotool
```Then create a launcher, I assume you know how, and enter a command like this (shortcut to run a terminal):
```
xdotool key Ctrl+Alt+t
```

---

### Post by hart02 on 2011-02-07
Hooray It works.Thanks:KS

---

