---
title: "Compiz settings are reset every session"
date: 2010-10-09
forum: General Help
---

### Post by Arancaytar on 2010-10-09
Since a while ago, any changes I make to my Compiz settings are not remembered when I log in again.

On starting a new gnome session, Compiz is firstly always disabled ("Visual Effects" in gnome-appearance-properties is set to "None"). I can enable the "Extra" option, but when I open gnome-appearance-properties a second time, the option is not selected (although Compiz will now be running), and when I log out and back in, Compiz will be disabled again.

After enabling it manually, I find that secondly, the "Desktop Cube" largedesktop feature is replaced by "Desktop Wall". I can change this in ccsm, and the changes take effect immediately, but when I start ccsm a second time, the changes are gone (the "Desktop Cube" checkbox is unselected). After logging out and back in, the old settings are in effect again.

Since ccsm will forget the changes even before I log out, I suspect it is somehow unable to save them. I've tried looking at the stderr output of gnome-appearance-properties and ccsm, but haven't seen anything that looks relevant.

Is there a settings file I should be looking at? Something wrong with file permissions, perhaps?

---

### Post by anu815 on 2010-10-09
I had a similar problem and had no window borders after login.

What sorted it for me was to remove the .gconf and .gconfd directories and then restart.  The link below suggests that removing ~/.gconf/desktop/gnome/session/ might be enough.

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/559111](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/559111)

Removing the whole of the folders meant that some of my application settings got lost e.g. for Evolution so it'd be worth taking a copy of the folders and trying the more specific folder first.

---

### Post by Arancaytar on 2010-10-09
Thanks very much!

Moving out the desktop/gnome/session folder fixed part of the problem: When I close and reopen gnome-appearance-properties or the Compiz Config Settings Manager, the settings I changed are still selected.

Unfortunately, the main problem is still there: When logging out and back in, the settings still get reset. I'll have to dig a bit further, I guess.

---

### Post by Arancaytar on 2010-10-19
The compiz settings being reset was a side effect of using gnome-appearance-properties to set the Visual Effects to "Extra", in order to activate compiz, which failed to start automatically. This not only started compiz, but also reset the enabled and disabled modules (while leaving special settings like keyboard bindings alone).

Manually launching compiz in a terminal avoided this problem. Also, installing the package "simple-ccsm" added a "Custom" option to gnome-appearance-properties that activates compiz without affecting compiz settings. (This is a bit buggy; that "Custom" option should be there anyway since it is possible to customize compiz settings using the *normal* ccsm without installing simple-ccsm at all.)

In the meantime, the original problem preventing compiz from launching automatically has been fixed on my computer, so I'm done.

---

