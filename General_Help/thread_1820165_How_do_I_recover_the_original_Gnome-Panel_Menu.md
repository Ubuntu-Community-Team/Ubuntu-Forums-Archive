---
title: "How do I recover the original Gnome-Panel Menu?"
date: 2011-08-07
forum: General Help
---

### Post by sidewalkcynic on 2011-08-07
1) I installed the whole UbuntuStudio OS

2) When I reconfigured the Gnome-Panel Menu with all the application launchers, I deleted the twenty-some audio and video launcers in the Audio/Video menu because they are in the specific Audio Production and Video Production menus; and I just wanted to clear up the Audio/Video menu so it only had the medi players.

3) Well, what happened was that deleting the launchers in the native menu deletes the launchers in the secondary menus. So, now all the production apps are missing and I do not remember all the names so as to replace them. I have tried to recover the original menu with some terminal commands I have found on the Internet, but they don't restore the original application list.

Any ideas on how to recover the original list?

How about a text list of all the applications and Bin Execute command, and I will do it one at a time???

---

### Post by blueridgedog on 2011-08-08
If you deleted them with the menu editing tool, then the entries for them in the gconf database have been removed.  As the entries are not represented by a file structure, I can't think of a way to get them back without a re-install.  You could try and boot off of a LiveCD and copy the .gconf directory to your local hard drive, or create a new user and see if they new user has the settings you are after (odds are it will work for a new user).

---

### Post by knutschr on 2011-08-08
Have you tried reinstalling ubuntustudio-menu in Synaptic?

---

### Post by Sotanaht on 2011-08-08
If you could find a list of the programs that come pre-installed, you could manually replace them using the menu editor.

---

### Post by sidewalkcynic on 2011-08-09
Thanks for the ideas, I have already been doing it manually, and have most of what I need - anything I missed, I'll pick up later.

---

