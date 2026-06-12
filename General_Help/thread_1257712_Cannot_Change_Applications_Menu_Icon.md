---
title: "Cannot Change Applications Menu Icon"
date: 2009-09-04
forum: General Help
---

### Post by toejamfootball on 2009-09-04
I have tried to change the icon for the gnome menu using gconf-editor but it doesn't change.

I click use custom icon and then I type in the exact location of the icon I want to use. What am I doing wrong?

---

### Post by mike555 on 2009-09-04
Can't you just go to "System" > "preferences" > "main menu", find the one you want to change and click on it to highlight it, click on properties , click on the icon box and pick a new one ..............

---

### Post by toejamfootball on 2009-09-04
> **mike555 said:**
> Can't you just go to "System" > "preferences" > "main menu", find the one you want to change and click on it to highlight it, click on properties , click on the icon box and pick a new one ..............
I'm talking about the icon for the Menu itself, not the icons for application etc. in the menu. The Ubuntu cirle thing.

---

### Post by toejamfootball on 2009-09-04
Is it to soon to bump? Sorry if it is :)

---

### Post by defacto on 2009-09-04
[http://ubuntuforums.org/showthread.php?t=208457](http://ubuntuforums.org/showthread.php?t=208457) - hope that helps.

---

### Post by Vaphell on 2009-09-04
you can always try to find original one somewhere in /usr/share/pixmaps and replace it with your own :)

---

### Post by nbtrap on 2009-09-05
Your icons for the menu are at /usr/icons/<theme name>/places

The default ubuntu icon theme is Human. Assuming your menu bar is the default size (24 pixels), you want back-up the file "start-here.png" to something like "start-here_bu.png" then override "starthere.png" with whatever icon you want. Then run:

```

killall gnome-panel

```

and viola.

---

### Post by toejamfootball on 2009-09-05
> **nbtrap said:**
> Your icons for the menu are at /usr/icons/<theme name>/places

The default ubuntu icon theme is Human. Assuming your menu bar is the default size (24 pixels), you want back-up the file "start-here.png" to something like "start-here_bu.png" then override "starthere.png" with whatever icon you want. Then run:

```

killall gnome-panel

```

and viola.
That worked, thanks!, I had to replace the start-here icon in the gnome/24x24 folder.

Cheers!

---

