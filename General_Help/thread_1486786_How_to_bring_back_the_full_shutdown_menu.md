---
title: "How to bring back the full shutdown menu?"
date: 2010-05-18
forum: General Help
---

### Post by hiacynt on 2010-05-18
Heyo, I have just upgraded to lucid and the first thing that I noticed was that the different shutdown options (Logout, Restart etc.) disappeared from the user-switch menu (at least that's how I think it is called) where they were located previously under karmic. Logout and Shutdown are placed under the System menu currently, and they work fine, but my question is how to show all (or some) of the shutdown options in the System or user menu? I dislike going through the dialog and prefer to choose my action directly from the menu.
I have tried removing and readding the user-switch applet, to no avail. I tried adding menu items to both the system menu and the user menu, to no avail either. I'm pretty sure it can be easily done, probably via gconf-editor but I could not find the appropriate options anywhere.

---

### Post by philinux on 2010-05-18
In gconf-editor click on Edit>Find then type in "Search For" shutdown and tick both boxes below. ;)

---

### Post by hiacynt on 2010-05-18
Thanks for the advice, but it did not have any effect, even after restarting. The 2 options that I found with gconf were 'suppress_shutdown_menuitem' and 'suppress_logout_restart_shutdown', were these what you referred to?

---

### Post by philinux on 2010-05-18
> **hiacynt said:**
> Thanks for the advice, but it did not have any effect, even after restarting. The 2 options that I found with gconf were 'suppress_shutdown_menuitem' and 'suppress_logout_restart_shutdown', were these what you referred to?

Correct, the key suppress_shutdown_menuitem should be unticked if you want shutdown to appear in the indicator applet.

The other one does this. Suppress the dialogue to confirm logout, restart and shutdown action.

The method for finding keys was what I was showing you.

---

### Post by hiacynt on 2010-05-18
Thanks, I got it solved now, although I had to switch the system language from my local to english to find the right applet. Cheers!

---

