---
title: "Can't Add New Shortcuts"
date: 2010-08-27
forum: General Help
---

### Post by Qoppa on 2010-08-27
Hi all,
I recently installed Ubuntu 10.04 (with Gnome) and everything went smoothly.  Very nice.  Now I'm trying to add some additional keyboard shortcuts, but the new ones I add don't work.  I can change the keybindings for existing shortcuts (for example, I changed goto workspace 1 to Alt+1 and this works), but I can't add a new shortcut.  Specifically, I'm trying to make Alt+F1..F4 move current window to workspace 1..4 but this won't work.  Nothing happens when I press the shortcut.  Same problem if I try to add a shortcut to any other command that didn't already have one.  Any ideas?

---

### Post by Qoppa on 2010-08-28
Anybody have any ideas?  I can post more info if needed.

EDIT: Partly solved!  If I go System->Preferences->Appearance and then set the visual effects to None, then they keyboard shortcuts work.  However, on normal and high (I had it on high), the send to workspace keybindings stop working.  I'm not sure, but I think it may have something to do with using no visual effects means use Metacity as the WM and Normal and High use Compiz, and the keybindings I set only apply to Metacity.  I think.  Next step is to see how to make these keybindings work with Compiz.

EDIT 2: Yeah, this would be the problem.  The keybindings that you set in System->Preferences->Keyboard Shortcuts are Metacity shortcuts, so they don't work with Compiz enabled.  Fixed for the most part now I think.

---

