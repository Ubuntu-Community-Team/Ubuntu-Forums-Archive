---
title: "Can't uninstall themes completely:Please help!"
date: 2010-06-21
forum: General Help
---

### Post by jre6 on 2010-06-21
I use Ubuntu 9.04 (Jaunty Jackalope). I recently installed four themes, [Mac4Lin]("http://gnome-look.org/content/show.php/Mac4Lin+ver.0.4+GTK+Metacity+Theme?content=71999"), [Tigris]("http://gnome-look.org/content/show.php/Tigris?content=75276"), [Raptor Slickness remix]("http://gnome-look.org/content/show.php/Raptor+%28Slickness+remix%29?content=86048") and [SlicknesS]("http://gnome-look.org/content/show.php/SlicknesS?content=71993"). I dragged them into the Appearance Preferences window to install them (in the Themes tab). I didn't like the themes and uninstalled them. But, while I was customising the original theme (Human), I saw that window controls and borders of the theme were not uninstalled ([1st attachment]("http://ubuntuforums.org/attachment.php?attachmentid=161085&stc=1&d=1277123089")). Also, if I want to reinstall the themes, I get an error ([2nd attachment]("http://ubuntuforums.org/attachment.php?attachmentid=161086&stc=1&d=1277123089")). I have checked if any folders named after these themes were there in "/usr/share/themes", but didn't find any. How am I to uninstall these themes completely?

---

### Post by VCoolio on 2010-06-21
Did you check in ~/.themes? (~ stands for /home/username and . means hidden file) If you 'install' a theme.tar.gz by dragging into the appearance window, or choosing install there, all that happens is that they are extracted to ~/.themes (or ~/.icons). You don't enter a password, so it couldn't be in your system directories.

---

### Post by jre6 on 2010-06-21
Thanks VCoolio. Your advice worked. Removing directories of the "~/.themes" worked. For this, nautilus must be executed through root terminal and "home/username/.themes" has to be put into the location bar and all the folders must be deleted.

---

### Post by VCoolio on 2010-06-22
> **jre6 said:**
> Thanks VCoolio. Your advice worked. Removing directories of the "~/.themes" worked. For this, nautilus must be executed through root terminal and "home/username/.themes" has to be put into the location bar and all the folders must be deleted.

There is no root necessary here; it's all in your user section. But glad it worked.

---

