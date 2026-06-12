---
title: "change home folder icon."
date: 2011-12-12
forum: General Help
---

### Post by soryu on 2011-12-12
how do i change the home folder icon in unity?

or any other icon in unity.

---

### Post by lechien73 on 2011-12-12
You can edit the .desktop files in /usr/share/applications

So, for example, to change the home folder icon:

```
gksu gedit nautilus-home.desktop
```

Change the icon= line to the path of a new icon. You may have to log out and back in for this to take effect.

---

### Post by soryu on 2011-12-12
i went to
 /usr/share/applications but unable to change it from there.

i put the code in the terminal and dragged the icon over but i get an error.

i didn't find the = line path

---

### Post by lechien73 on 2011-12-12
Ok, let's say you have an icon called home-icon.png in your home directory, and let's say that your Ubuntu username is soryu.

You would type:

```
gksu gedit /usr/share/applications/nautilus-home.desktop
```

Then you would change the line that says:

```
Icon=user-home
```

to read:

```
Icon=/home/soryu/home-icon.png
```

Afterwards, save and close the nautilus-home.desktop file. Log out of Ubuntu and log back in again.

---

### Post by soryu on 2011-12-12
thanks for the help.
 i'm just gonna keep it the way it is

---

### Post by lechien73 on 2011-12-13
No problem. If you get chance, could you please use the **Thread Tools** menu at the top of the page, and mark this issue as [SOLVED]?

Thanks

---

