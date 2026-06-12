---
title: "Cannot change theme"
date: 2011-01-18
forum: General Help
---

### Post by mathjazz on 2011-01-18
I have Ubuntu 10.10 installed and I use NVIDIA GeForce GT 430 with proprietary drivers. The strange thing that happend after installation and is still present is that all applications use some ugly gnome theme and icons, except for "Appearance Preferences" windows, which looks just fine.

Plese see the screenshot:
[http://www.dropmocks.com/mPbHE](http://www.dropmocks.com/mPbHE)

I tried changing theme, but only window border gets changed. Controls, icons and color stay the same.

---

### Post by mathjazz on 2011-01-18
I just figured out that the theme works perfectly fine on the login screen and when I login with another account.

---

### Post by mathjazz on 2011-01-18
But after I reinstalled light-themes and tried logging into this other account, the theme was broken again. I also created third account, removed .gconf folder and rebooted.

Nothing helps.

---

### Post by mathjazz on 2011-01-18
But after I reinstalled light-themes and tried logging into this other account, the theme was broken again. I also created third account, removed .gconf folder and rebooted.

Nothing helps.

---

### Post by Frogs Hair on 2011-01-18
See if this tread is related.[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

---

### Post by mathjazz on 2011-01-18
It was, thanks!

I went to System -> Preferences -> Startup Applications and added gnome-settings-daemon and now I'm happy.

---

### Post by mathjazz on 2011-01-18
It was, thanks!

I went to System -> Preferences -> Startup Applications and added gnome-settings-daemon and now I'm happy.

---

