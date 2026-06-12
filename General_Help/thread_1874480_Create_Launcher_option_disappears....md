---
title: "Create Launcher option disappears..."
date: 2011-11-03
forum: General Help
---

### Post by shantiq on 2011-11-03
on my new Oneiric desktop when i right-click i get offered a restricted set of options at the moment


see below


no create launcher
no resize icon



how can i set it back to all options offered?

---

### Post by stinkeye on 2011-11-03
```
sudo apt-get install --no-install-recommends gnome-panel
```

Save this script as **Create_Desktop_launcher** for a right click nautilus script item.
```
#!/bin/bash

gnome-desktop-item-edit ~/Desktop/ --create-new
```
Place in ~/.gnome2/nautilus-scripts/ and make executable.

The resize icon is there when you click on a desktop icon.

---

### Post by Mark Phelps on 2011-11-03
While that command works, it is insufficient in the vanilla 11.10 install because it uses a gnome-panel binary that does not exist in your install.  I know because I ran into this myself.

You can either install gnome-panel, or if you want the ability to display and edit the menus using the former Ubuntu look and feel, you should install alacarte.

You can find either using the Ubuntu Software Center.

---

### Post by stinkeye on 2011-11-03
> **stinkeye said:**
> ```
sudo apt-get install --no-install-recommends gnome-panel
```


-

---

### Post by shantiq on 2011-11-03
> **stinkeye said:**
> ```
sudo apt-get install --no-install-recommends gnome-panel
```

Save this script as **Create_Desktop_launcher** for a right click nautilus script item.
```
#!/bin/bash

gnome-desktop-item-edit ~/Desktop/ --create-new
```
Place in ~/.gnome2/nautilus-scripts/ and make executable.

The resize icon is there when you click on a desktop icon.


thanx man the kamelzknackerz
i suppose one can add other things too that way? 
:KS

---

### Post by stinkeye on 2011-11-03
> **shantiq said:**
> thanx man the kamelzknackerz 
i suppose i can add all sorts that way:KS
Yep , you'll find heaps to browse through here...
[**_[COLOR="DarkRed"]http://gtk-apps.org/index.php?xcontentmode=188[/COLOR]_**]("http://gtk-apps.org/index.php?xcontentmode=188")

---

### Post by shantiq on 2011-11-03
marvelous 

==============================================

---

