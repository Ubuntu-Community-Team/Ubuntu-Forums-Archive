---
title: "Unable to install anything"
date: 2011-04-05
forum: General Help
---

### Post by chand.sethi77 on 2011-04-05
When ever I try to install anything using terminal like apt-get install showtime-theme , the following error occurs:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdesktop-agnostic-cfg-gconf: Depends: libdesktop-agnostic0 (= 0.3.90-0ubuntu1) but it is not going to be installed
  libdesktop-agnostic-fdo-glib: Depends: libdesktop-agnostic0 (= 0.3.90-0ubuntu1) but it is not going to be installed
  libdesktop-agnostic-vfs-gio: Depends: libdesktop-agnostic0 (= 0.3.90-0ubuntu1) but it is not going to be installed
  showtime-theme: Depends: icon-showtime-theme but it is not going to be installed
                  Depends: gtk-showtime-theme but it is not going to be installed
                  Depends: metacity-showtime-theme but it is not going to be installed
                  Depends: emerald-showtime-theme but it is not going to be installed
                  Depends: wallpaper-showtime-theme but it is not going to be installed
                  Depends: gnome-showtime-theme but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```And when I use software center,  the following error occurs:
```
 The system packages are broken. 
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f 
```

---

### Post by nothingspecial on 2011-04-05
Did you try doing what the error message suggests and run

```
sudo apt-get install -f
```

---

### Post by chand.sethi77 on 2011-04-05
Tried. still not working. How to disable 
**third party repositories**

---

### Post by chand.sethi77 on 2011-04-05
Hey thanks.. I was doing a sill mistake.. i was using 
sudo apt-get install -f cairo-dock
instead of only
sudo apt-get install -f

---

### Post by nothingspecial on 2011-04-05
Depends on how you added them

either put a # infront of them in /etc/apt/sources.list

or remove them from /etc/apt/source.list.d if you used apt-add-repositry

or do it from synaptic package manager (can't remember the exact steps for that)

---

