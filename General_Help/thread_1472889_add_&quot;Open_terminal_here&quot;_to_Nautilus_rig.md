---
title: "add &quot;Open terminal here&quot; to Nautilus right click menu?"
date: 2010-05-04
forum: General Help
---

### Post by Rubicon421 on 2010-05-04
I know there are some distros that have a feature to open a new terminal in the current Nautilus directory. I think I saw it in Mint or maybe some KDE or XFCE distro. I'm trying to find a way to add this to Ubuntu/Gnome, either in the right click menu or the Nautilus tool bar. 

Anyone know of a script or package that can do this?

---

### Post by ks07 on 2010-05-04
[apt://nautilus-open-terminal](apt://nautilus-open-terminal)

^-- It's in the universe repo. :KS

---

### Post by Rubicon421 on 2010-05-04
> **ks07 said:**
> [apt://nautilus-open-terminal](apt://nautilus-open-terminal)

^-- It's in the universe repo. :KS


Thanks, I actually found that right after my post. I have it installed but don't see anything new. I haven't restarted yet so I'm going to give that a try.

[EDIT] That was it. It's right there in the context menu now. SWEET!

---

### Post by mikehattingh on 2010-06-01
What they mean is:
In a terminal type
```
$ sudo apt-get install nautilus-open-terminal
```
Log out and back in (Ctrl + Alt + Backspace)
"Open in Terminal" should now be in the Nautilus context menue.

---

