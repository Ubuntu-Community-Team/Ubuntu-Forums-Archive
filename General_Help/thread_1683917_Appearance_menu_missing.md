---
title: "Appearance menu missing"
date: 2011-02-08
forum: General Help
---

### Post by EpicTone on 2011-02-08
Hello.
I woke up today to find that System>Preferences>Appearance is missing. I navigated to /usr/share/applications and gnome-appearance-properties.desktop is missing. Is there any way to get it back?

Thanks

---

### Post by SoFl W on 2011-02-08
Is there an option in System-> Preferences-> Main Menu?

---

### Post by EpicTone on 2011-02-08
> **SoFl W said:**
> Is there an option in System-> Preferences-> Main Menu?
i mean the gnome-appearance-properties.desktop is MISSING. therefor there would be no link to it, and i already checked the folder it would be located in, as i said in my previous statement.

---

### Post by Mad dog on 2011-02-08
Make your own launcher with the command gnome-appearance-properties and put it in the location it's supposed to be.

---

### Post by alas-poor-yorick on 2011-08-05
Mad dog, the problem is gnome-appearance-properties somehow got uninstalled. Running it from a command line returns "command not found". I have this problem too. How do we reinstall it? It doesn't seem to be in gnome-control-center.

EDIT: I meant gnome-control-center

---

### Post by CatKiller on 2011-08-05
reinstall *gnome-control-center*.

---

### Post by alas-poor-yorick on 2011-08-05
it doesn't work. I reinstall it, and when I type gnome-appearance-properties, it just tells me to install gnome-control-center even though it is already installed and at the latest version.

---

### Post by alas-poor-yorick on 2011-08-05
I fixed it. I had tried to remove Gnome 3 by just typing sudo apt-get remove --purge gnome-shell. That broke everything. I followed the instructions here: [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3) and it went back to normal.

---

