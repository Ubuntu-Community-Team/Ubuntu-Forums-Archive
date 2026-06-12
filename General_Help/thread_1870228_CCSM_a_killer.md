---
title: "CCSM a killer"
date: 2011-10-26
forum: General Help
---

### Post by StevenD on 2011-10-26
I decided the CCSM is a killer and so I'm not even going to bother with it. I'm not even going to try and reduce the size of the Launcher icons until another method is realized. 48 is silly big. I will just wait.:(

---

### Post by wolfen69 on 2011-10-26
I believe they reduce in size as you add more launchers. At least they do with gnome-shell.

---

### Post by mc4man on 2011-10-26
> **StevenD said:**
> I decided the CCSM is a killer and so I'm not even going to bother with it. I'm not even going to try and reduce the size of the Launcher icons until another method is realized. 48 is silly big. I will just wait.:(

You should be able to go into the unity plugin settings with anything bad happening in ccsm

If you want to go directly there try
Alt+F2 
for the  command use
```
about:config
```

Or all the unity settings can be adjusted without using ccsm or even having compizconfig-settings-manager installed

You'd just use gconf-editor (may need to be installed
Browse to apps > compiz-1 > plugins > unityshell > screen0 > options & double left click right on where it says "icon_size"
Use the edit box to adjust.
Afterwards you may need to log out/in to realize changes

---

