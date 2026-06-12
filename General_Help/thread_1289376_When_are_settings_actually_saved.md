---
title: "When are settings actually saved?"
date: 2009-10-12
forum: General Help
---

### Post by donsy on 2009-10-12
Frequently I find it educational to open up a properties window to an app just to browse the various settings and options. I'm curious about the following points: 

1. Even if I don't change anything is the config file still written if I click the Close button?

2. Does clicking the X box on the window cause the same same behaviour as clicking the close button?

3. Suppose I make more than one change. Is the config file written after each individual change or only once after clicking the Close button?

---

### Post by undecim on 2009-10-12
In most cases, options are updated in real time, though this will be different for some applications. In this case, the configuration file is saved immediately when you change something.

In general, if there is an "Okay" or "Apply" button in the windows, The configuration isn't updated until you press one of those two buttons. In most other cases, it is updated as you change settings in the preferences window.

If you are worried about breaking the program you are exploring, you can always make a backup of the configuration file, play around with the graphical configuration, then restore the old one later if you find it necessary.

Most applications will store settings in a "dotfile" or "dotfolder" in your home directory. For example, Mozilla Firefox stores its data in the ".mozilla/" folder in your home directory (notice the period or "dot" in front of the folder name) To see these in nautilus, you will need to press CTRL+H to view them. (dotfiles are hidden by default)

Some others, especially desktop apps will store configurations in a folder in the .config folder in your home directory. (Compiz stores its settings at .config/compiz/)

Some other places you might find config folders:
.gnome2/ (especially for gnome specific apps
.gconf/apps (these settings are also available through the gconf-editor program)
.kde4 (for kde specific apps)

If you can't find the configuration file, you can consult the applications documentation.

---

