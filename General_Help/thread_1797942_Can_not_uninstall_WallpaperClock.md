---
title: "Can not uninstall WallpaperClock"
date: 2011-07-05
forum: General Help
---

### Post by dsanjoy on 2011-07-05
I installed a WallpaperClock (which I downloaded in .rar.bz2 format and saved) via screenlet Ubuntu 11.04. But now I can not uninstall it. Any help would be great. I tried to find it in installed software section using Ubuntu Software Center, but it does not show anything.

---

### Post by Archy1987 on 2011-07-05
try to reinstall the software center in package manager, maybe it will help you. Anyway, package manager is the place, where you can install/reinstall/uninstall anything, that you have installed.

---

### Post by cornelis1 on 2011-07-05
You have to manually delete the folder containing the wallpaperclock screenlet that is located in the hidden .screenlets folder in your home folder.

---

### Post by dFlyer on 2011-07-05
From a terminal in your home folder try:

rm -rf .screenlets

---

### Post by dsanjoy on 2011-07-07
Hi All ! Thanks for your help. I tried all of the above but it does not solve my problem. Let me state my problem more clearly. First I installed "screelets" and then "screenlets-pack-all". Then I download a wallpaperclock theme from the following link

[http://gnome-look.org/content/show.php/A+little+motivation+wallpaper+clock?content=80396](http://gnome-look.org/content/show.php/A+little+motivation+wallpaper+clock?content=80396)

Next I opened screenlet manager and installed the above mentioned theme (which I downloaded in .tar.bz2 format). Now my problem is, I do not like that wallpaper theme. I wanted to remove it completely. Even if I uninstall "screelents" and "screenlets-pack-all" completely using synaptic package manager and manually remove .screelets and .WallpaperClock from my home, next time when I reinstall "screelents" and "screenlets-pack-all" the WallpaperClock automatically picks up that unwanted theme. I hope I could state my problem clearly. In short , I want wallpaper clock widget but I want to remove the theme I installed.

---

### Post by CatKiller on 2011-07-07
So you don't want to remove WallpaperClock, you just want to change the theme? Just install a new theme, potentially in the same way you installed the previous one.

---

