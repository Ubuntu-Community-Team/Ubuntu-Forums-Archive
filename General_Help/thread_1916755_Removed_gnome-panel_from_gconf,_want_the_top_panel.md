---
title: "Removed gnome-panel from gconf, want the top panel to load on startup again"
date: 2012-01-28
forum: General Help
---

### Post by AlvitrValkyrie on 2012-01-28
Ubuntu 10.04

Everyone keeps talking about "restoring" the panel to default." No, I don't want both panels back, nor do I want either of them back with their normal configuration. I deleted the bottom panel for AWN, and decided to remove the top panel from the required components folder in gconf-editor. 

When I try to edit the key for "panel | gnome-panel" via gconf-editor, it tells me "The key is not writable." Another question is why is the gnome-panel key already there, but the panel isn't starting up on boot?

After running 
```

$ gconftool-2 --shutdown 
$ rm -rf ~/.gconf/apps/panel 
$ pkill gnome-panel
```[A previous answer] The panels STILL don't show up on reboot, and now I get an error "The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"." whenever I DO load the panels by typing "gnome-panel" into GnomeDO (I had a single launcher--the terminal--on the panel.)

What I need:
(1) A fix for that error
(2) To have ONLY the top panel load on reboot.

I'm trying to get my system ready so I can build a custom iso, and I don't want to rebuild my ubuntu install for the nteenth time.


I can change the value for the panel key after I click "Unset key," but then I get this error:
```
Could not change key value. Error message:
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/desktop/gnome/session/required_components/panel' set in a read-only source at the front of your configuration path
```

---

### Post by ajgreeny on 2012-01-28
I don't think you can get back to your wished for panel configuration in one easy step if you don't have a backup of the hidden ~/.gconf folder, where all that is kept.

You could try removing the ~/.gconf/apps/panel folder, and then logging out and back in again, but that should send you back to the default 2 panel setup, which you will then have to change back to what it used to be or to whatever you want.

The moral of this, is to make sure you have good backups of your home, including all your hidden files and folders.

---

