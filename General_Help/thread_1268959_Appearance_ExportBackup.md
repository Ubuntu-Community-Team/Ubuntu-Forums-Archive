---
title: "Appearance Export/Backup"
date: 2009-09-17
forum: General Help
---

### Post by HammerOfDoubt on 2009-09-17
I broke my Ubuntu and I'm going to reinstall (was going to do it anyway).

I want to export or back up my theme/appearance settings. The "Save As" option in the Appearance menu just saves it somewhere internally. Is there a way to save it as a stand alone file so I can load it up once i re-install?

---

### Post by undecim on 2009-09-17
All your settings are saved in your home directory. You can save all of your applications settings, documents, appearance, etc. by backing up your home directory. (This is why a lot of people put their home directory on a seperate partition. It gives you the freedom to move to new distros without losing all that stuff)

For appearance settings, I think that is under the ".gconf" folder in your home directory (you need to enable viewing hidden files to see it. Use Ctrl+H in a GUI, or use ls -a in a CLI)

It might also be under .gnome2... Im not sure which.

Either way, if you have the external drive space, I would recommend backing up your entire home directory if you are reinstalling because of a broken OS.

---

