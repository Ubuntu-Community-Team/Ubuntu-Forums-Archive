---
title: "GUI/COMPIZ problems - everything suddenly on one workspace, settings all gone"
date: 2010-12-31
forum: General Help
---

### Post by MorrisseyJ on 2010-12-31
Hi i have been having a problem with what i think is my GUI.

All of a sudden my system will freeze/flicker for a few moments and i'll find that i all my open windows have been placed on the first workspace (which i will suddenly be looking at). My wobbly windows effects will have stopped, desktop cube has gone and i can't drag windows to another workspace (i can only send them there with a right click --> 'move to workspace...').

If i go into COMPIZ, 'desktop cube' and 'rotate cube' have become unchecked. If i recheck them and close, they still don't seem to work. Even when i go back into COMPIZ and find that they are still checked.

All i can seem to do is reset the GUI to its default using 

> **rm -rf .gnome .gnome2 .gconf .gconfd .metacity** from [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

and then redo all my settings. 

One note, on another solution: possibly there is some driver problem as when i go into 'Appearance Preferences' and try to recheck 'extra' visual effects, i get a dialogue box telling me that the system is searching for drivers. Eventually i get wobbly windows back. Then if i go into compiz, boxes are all unchecked again, but this time if i re-check them they stay checked, and i get cube back. 

The above makes me think that at some point my driver is crashing, but i don't know why, or which driver. I can't trace when the problem started, although its fairly recent. Maybe its to do with the new kernel - although it seems to happen when i boot to older ones as well. It also doesn't appear to be triggered by anything that i can identify.

Can anyone advise or corroborate the issue i am having. 

If this is already on another thread, sorry i missed it. I couldn't find the appropriate search terms. Do please post a link to that thread here, should it exist.

Thanks.

---

