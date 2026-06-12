---
title: "Change default terminal size?"
date: 2009-07-08
forum: General Help
---

### Post by wqawasmi on 2009-07-08
is it possible to change the default terminal start up size to something custom like 60x40??

---

### Post by DeMus on 2009-07-08
> **wqawasmi said:**
> is it possible to change the default terminal start up size to something custom like 60x40??

Yes.

In terminal click on menu Terminal, at the bottom of the drop-down menu you find 4 possibilities. Choose the one you like.
The next time it will open again at the default size however.

---

### Post by kerry_s on 2009-07-08
sure just add it to the launcher " --geometry 60x40 "

**gnome-terminal --geometry 60x40**

if you read the man page it will tell you the other goodies you can use.
**man gnome-terminal**

to edit the launcher use the right click> edit or properties(if it's a desktop/panel icon)

---

### Post by fkrogh on 2009-07-27
Editing the profile for the gnome-terminal, checking the "Run a custom command instead of my shell", and putting 
/usr/usr/bin/gnome-terminal --geometry 80x50
or 
/usr/bin/gnome-terminal --geometry=80x50
in the little window for that results in a gnome terminal of the correct size opening, and then getting replaced by another of the same size, etc., etc.  Removing the check mark on "Run a custom command instead of my shell" in the window for editing the profile stops this and leaves the desired window.  Of course it would be easier just to drag the window to the desired size.  Does anyone have an idea why this is working as it does?  Thanks,
Fred

---

### Post by phenix777 on 2009-07-27
The way given above, as in adding it to the launcher (e.g. "gnome-terminal --geometry 80x43") works great for modifying the window size produced by a launcher (i.e. button).
However, there is a problem with that solution when you want to launch the terminal from a shortcut-key and still have the modified size.

Here's the solution.
Open a terminal and type:
```
gconf-editor
```This will bring up a window.  On the left side, navigate to:
**/desktop/gnome/applications/terminal**

For the key with **Name=Exec** modify the <strong>Value</strong> to be:
```
gnome-terminal --geometry=80x43
```(or similar depending on the exact size you want)

Now, when you launch the terminal via a shortcut key (**System->Preferences->Keyboard Shortcuts**) it will have the desired dimensions.

---

### Post by fkrogh on 2009-07-28
Thanks for this.  Unfortunately, that computer will not be accessed for awhile.  When it is I'll give this a try.

---

