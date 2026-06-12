---
title: "Way to reset all ubuntu settings without loosing programs, and documents?"
date: 2009-09-21
forum: General Help
---

### Post by gksudo on 2009-09-21
Hello,
I was wondering if there was a way to reset all ubuntu settings, cache,ect. ect. Without loosing programs? Thanks.

---

### Post by BraedenNaylor on 2009-09-21
> **gksudo said:**
> Hello,
I was wondering if there was a way to reset all ubuntu settings, cache,ect. ect. Without loosing programs? Thanks.

Please use google. First result when searching for "reset all ubuntu settings"

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by unutbu on 2009-09-21
Generally, all personal configuration settings are saved in files or directories that start with a period (so-called dot files).

For example, these 3 directories (inside your home directory) hold the settings
for your GNOME desktop
```

~/.config
~/.gnome
~/.gconf

```
If you rename these directories to say, 
```

~/.config-old
~/.gnome-old
~/.gconf-old
```

then log out and then log back in, GNOME will automatically regenerate these directories and give you "factory default" settings, like when you first installed Ubuntu.

Many applications also save their settings in an eponymous directory. For example, GIMP saves settings in some dir like ~/.gimp-2.6 and firefox saves settings in ~/.mozilla/firefox. If you were to rename all your dot-files, you will reset all your personal Ubuntu settings without losing programs or documents.

---

### Post by gksudo on 2009-09-21
I was going to use google but I went to the forums to verify that I wouldn't lose all my programs. Thanks.

---

### Post by unutbu on 2009-09-21
If you are worried about losing data (like firefox bookmarks), just rename the dot-files instead of deleting them. Then it is easy to recover from mistakes. When you are satisfied that the resetting was successful, then you can delete the renamed directories.

---

### Post by gksudo on 2009-09-22
Thanks. I will do that.

---

### Post by dcstar on 2009-09-23
> **BraedenNaylor said:**
> Please use google. First result when searching for "reset all ubuntu settings"

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

Yep, great idea if you want to lose ALL your Evolution stuff.

---

