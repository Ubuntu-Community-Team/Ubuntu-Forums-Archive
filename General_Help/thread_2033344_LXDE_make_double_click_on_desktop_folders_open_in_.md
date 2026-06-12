---
title: "LXDE: make double click on desktop folders open in nautilus?"
date: 2012-07-26
forum: General Help
---

### Post by crackers8199 on 2012-07-26
so, i've got ubuntu 12.04 installed (that's why i used ubuntu as prefix rather than lubuntu)...but i've also got lxde running as my default desktop environment.  i also much prefer nautilus as a file manager over pcmanfm...

i've gone through a bunch of steps to set nautilus as the default file manager...including menu, accessories, right click file manager, and change to nautilus in properties.  i've got an icon in the app launch bar for nautilus as well...but folders i create on the desktop are still opened by pcmanfm when i double click.  

i've tried right-click on them and changing the default that way, i've also tried changing the default using xdg-mime - and verified that it took.  still opens them in pcmanfm...

is there any way to get double clicking a folder on the desktop in this case to open in nautilus instead of pcmanfm?  i really don't like gnome3 and while i've used xfce for a while, lxde seems like a really nice alternative...but this is one thing that really bothers me.  can anyone help me out?

---

### Post by crackers8199 on 2012-07-26
anyone have any idea if there's a way to make this happen?

---

### Post by brainwash on 2012-07-26
How about using nautilus to manage the desktop instead of pcmanfm? Currently I'm running Xubuntu with nautilus as default file manager and  desktop manager. I'm not familiar with LXDE, so you will have to do some research on your own.

Basically you will have to stop "pcmanfm --desktop" from running on login and create a new autostart launcher containing:
```
Exec=nautilus -n
```

Last but not least you will have to enable the desktop icons via *gsettings*.

---

### Post by crackers8199 on 2012-07-26
> **brainwash said:**
> How about using nautilus to manage the desktop instead of pcmanfm? Currently I'm running Xubuntu with nautilus as default file manager and  desktop manager. I'm not familiar with LXDE, so you will have to do some research on your own.

Basically you will have to stop "pcmanfm --desktop" from running on login and create a new autostart launcher containing:
```
Exec=nautilus -n
```

Last but not least you will have to enable the desktop icons via *gsettings*.

nice idea, and i've got that working now...thanks!

one last question - any way i can change the text on desktop icons from black to white?

---

### Post by brainwash on 2012-07-26
> **crackers8199 said:**
> one last question - any way i can change the text on desktop icons from black to white?
Simply edit your current gtk3 theme (/usr/share/themes/<name>/gtk-3.0/) and add following lines:
```
.nautilus-desktop.nautilus-canvas-item {
    color: #ffffff;
}
```

---

### Post by crackers8199 on 2012-08-22
that didn't seem to work...am i editing the wrong file?

i've also switched to openbox with xfce4-panel, and that has added a whole new twist on things.

when i right click on the desktop and go to change desktop background (desktop drawn by nautilus), i get Ambiance as the theme used by the UI.  that's the theme i should be changing, right...?

i added the line to /usr/share/themes/Ambiance/gtk-3.0/gtk.css and it didn't do anything...am i changing the wrong file?

also, nautilus is missing icons...is there a way to fix that?  i ran lxappearance and that brought the icons into the panel (they were previously missing there as well), but they're still not showing up in nautilus...any ideas?

---

