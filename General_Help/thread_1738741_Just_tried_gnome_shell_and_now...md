---
title: "Just tried gnome shell and now.."
date: 2011-04-25
forum: General Help
---

### Post by warrior_juggalo on 2011-04-25
My Applications menu looks retarded, screen shot included.

I have my Fedora system set up EXACTLY how i like it, Looks, Speed Functionality, PERFECT, It FEELS good to use, Something little like this throws it all out.

---

### Post by 3rdalbum on 2011-04-25
Just PM'ed warrior_juggalo telling them that there's no screenshot included.

---

### Post by WorMzy on 2011-04-25
> **warrior_juggalo said:**
> Something little like this throws it all out.

Which is why you shouldn't use your main OS for trying things out like this. Some of your settings have probably been overwritten, your best bet is probably to remove all the config files relating to gnome from your home folder, then start from scratch again.

Start by removing (or renaming if you'd prefer to keep backups)

~/.local/share/desktop-directories
~/.local/share/applications
~/.gconf/apps/panel

Then log out an back in.

---

