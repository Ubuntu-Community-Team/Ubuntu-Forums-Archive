---
title: "Strange problem with KDE apps"
date: 2009-11-15
forum: General Help
---

### Post by arnab_das on 2009-11-15
Here's the thing. I had unfortunately removed Konquerer and other KDE apps from the GNOME menu from alacarte. but now, even when i remove and reinstall it i dont find the programs in the menu or in alacarte! :( why is that?

---

### Post by Zorael on 2009-11-15
This is sort of related to [this post](http://ubuntuforums.org/showthread.php?p=8320901).

Basically, your user has a bunch of text files each containing information about an application that overrides the system-wide information about that application, in terms of the applications' names, prevalence in the menu, what filetypes they can open, etc. These files are .desktop files.

An application's system-wide file is installed (into **/usr/share/applications**) when the appliaction itself is installed, as it's part of the package. On the other hand, your user-specific override file is *created* as soon as you, for instance, make a change to the applications's menu entry. Now, even when removing an application, any potentially existing files in users' directories containing overrides for it will remain, which can leave ghost menu entries of apps no longer installed, and likewise missing entries (like you're experiencing). Removing an app from the menu doesn't remove its file, but rather makes the file say "should not show in the menu". Even after having reinstalled the app, your file will still exist and keep telling the menu not to show it.

What you want to do is look into **~/.local/share/applications/** and find whatever .desktop files in there whose names rhyme with Konqueror and your other KDE apps, and remove them. Then they will no longer override the system-wide defaults, and your menu entries should pop up again. You may need to run 'kbuildsycoca4' after having removed them to make the menu update.

---

### Post by arnab_das on 2009-11-15
thanks. everything working fine now.

---

