---
title: "Multiple Desktops"
date: 2010-05-15
forum: General Help
---

### Post by flipper9 on 2010-05-15
Okay, strange question.  I have 9 workspaces (desktops, not sure of the right terminology).  I would like it so that when a program on a particular desktop (say desktop #3) decides to display a modal dialog (such as a "success" dialog with an OK button you need to click) or a new window, I'd like those windows to be "forced" to the same desktop # (i.e. desktop #3) rather than displaying on the current desktop.

The problem is this, when I'm running multiple workspaces, I might be on a workspace that is using a program that I don't want interrupted (such as a impress presentation or a program that is always on top, such as a practice exam software program).  If I'm running a program on Desktop #3, I want all of the dialogs that "pop-up" to stay on Desktop #3, and not just popup wherever they want, especially on the workspace that I'm currently on.

Any suggestions on how to accomplish this (without suggestions like "you shouldn't be using multiple workspaces", "that seems silly", "turn off compiz and everything", and other nonsense)?

---

### Post by iponeverything on 2010-05-15
```
sudo apt-get install gconf-editor
```

then run:

```

sudo gconf-editor

```

If you don't see the option in there for that type of window control, it many not exist..

---

### Post by flipper9 on 2010-05-15
I flipped through a bunch of the options there, but nothing jumped out as related to this.  Maybe something in compiz settings or elsewhere?  I have no idea where to look, and have looked through the compiz settings manager to no avail...and haven't seen anything in gconf-editor. :(

---

### Post by flipper9 on 2010-05-16
Bump

---

