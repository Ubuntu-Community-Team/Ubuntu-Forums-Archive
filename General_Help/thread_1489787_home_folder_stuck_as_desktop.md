---
title: "home folder stuck as desktop"
date: 2010-05-21
forum: General Help
---

### Post by afrodeity on 2010-05-21
I've been trying to fix nautilus which is crashing, so deleted the ~/Desktop folder, thinking it would reset as in karmic, but not in lucid. Now have home folder as the desktop. Tried recreating ~/Desktop, but no luck. Gconf-editor no luck either since checking or unchecking the home folder as destop does nothing. Any ideas how to fix this problem?

---

### Post by -humanaut- on 2010-05-21
You need to go to /home/Username/.config/user-dirs.dirs

---

### Post by alecbenzer on 2010-05-21
I think you can fix this by editing ~/.config/user-dirs.dirs and changing the line
```
XDG_DESKTOP_DIR="$HOME"

```
replacing $HOME with $HOME/Desktop, or whatever.

---

### Post by afrodeity on 2010-05-21
> **alecbenzer said:**
> I think you can fix this by editing ~/.config/user-dirs.dirs and changing the line
```
XDG_DESKTOP_DIR="$HOME"

```
replacing $HOME with $HOME/Desktop, or whatever.

This is supercool, wow, it worked. :guitar:

You wouldn't perhaps know how to stop nautilus from crashing? Since the upgrade to lucid, I don't get a proper nautilus so I think it has something to do with the config, but now sure where to look?

---

