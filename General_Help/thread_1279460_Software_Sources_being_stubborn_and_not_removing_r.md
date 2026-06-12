---
title: "Software Sources being stubborn and not removing repository"
date: 2009-09-30
forum: General Help
---

### Post by gh4ever on 2009-09-30
Well, after trying to install apt-build for something, I didn't like it and uninstalled. What it didn't do, however, is remove the repository apt-build added in the installation. I tried removing it through the gui, nothing happened, I tried to gedit sources.list, only to find that the repository isn't listed there. Even after rebooting, it is STILL in the software sources. I even tried deleting the folder it was pointing to, only to be greeted with an error saying it couldn't find the folder and download from the repository.
The repository is this:
file:/var/cache/apt-build/repository apt-build main.

Many, many, many thanks in advance. I really owe a beer to the person who figures this out for me :D.

---

### Post by mac9416 on 2009-09-30
Perhaps it's a file in /etc/apt/sources.list.d/?

---

### Post by gh4ever on 2009-10-01
You were right! Thanks a bunch.
Now I feel really stupid about not poking around some more in that folder :D.

---

