---
title: "Changed Nautilus Background -&gt; Nautilus crashes"
date: 2011-03-30
forum: General Help
---

### Post by An Sanct on 2011-03-30
I've been messing with settings of nautilus via 
```
"Edit" > "Backgrounds and Emblems..."
```
and selected a background image.

And from that moment on, nautilus crashes (reloads) on almost every right click, menu opening, and almost any action, nautilus should do (as a file manager).


Has anyone experienced anything like this before and has a solution?

PS. Running Nautilus from Terminal and observing the output left me with a blank output ... no errors, no warnings, just reset.

---

### Post by blueridgedog on 2011-03-30
If you unselect the background image, does the issue persist?

---

### Post by An Sanct on 2011-03-30
Yes, I managed to deselect the image/pattern, by opening a Nautilus window, selecting "Edit" from the menu - this causes nautilus to crash. 
If I open another nautilus window quickly and select "Edit" with Alt+e and then scroll down the menu with my cursor keys to "Background and Emblems...", then it can be done.

Now, nautilus is "un-themed" (white) again, but sill crashes.

As mentioned above, moving my mouse cursor over the menu or right clicking also crashes nautilus :(, nautilus just went wild ...

PS. I also tried a reboot, if this where a simple temporary anomaly in the system.

---

### Post by blueridgedog on 2011-03-30
The following may help:

In a terminal...

```
mv ~/.gconf/apps/nautilus ~/.gconf/apps/nautilus.old
```

(basically deleting your nautilus profile)

Then restart.

If problem persists, then try:

```
sudo apt-get purge nautilus
sudo apt-get install nautilus
```

(uninstalling and reinstalling nautilus).

---

### Post by An Sanct on 2011-03-30
> **blueridgedog said:**
> The following may help:

In a terminal...

```
mv ~/.gconf/apps/nautilus ~/.gconf/apps/nautilus.old
```(basically deleting your nautilus profile)

Then restart.

Thank you! This part helped! :)

---

### Post by An Sanct on 2011-03-30
... fixed it ... another lesson ... well learned (I hope)

For anybody, browsing this, while it is in the archives ... I did the following stupid things:
-uninstalled nautilus
-didn't check if I reinstalled nautilus
-couldn't log in to the system anymore ...
-logged in and got right back to the login screen ... endlessly ...

and the solution was ...
-reinstalling gnome-shell

---

### Post by An Sanct on 2011-03-30
Another tip ... selecting "Open each folder in its own window" (on screenshot) makes nautilus go berserk...

---

