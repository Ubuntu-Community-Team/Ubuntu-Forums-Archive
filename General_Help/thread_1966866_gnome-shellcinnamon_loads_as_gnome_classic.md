---
title: "gnome-shell/cinnamon loads as gnome classic"
date: 2012-04-27
forum: General Help
---

### Post by Mr Nemo on 2012-04-27
I have gnome classic/shell and cinnamon installed on my system. Gnome shell and cinnamon will not load at all if selected and defaults back to gnome classic. I do have Nvidia w/ optimus, which could be the problem, but cinnamon and gnome shell worked perfectly before I upgraded to 12.04 (clean install). I haven't had much luck with google or other resources. Any help would be appreciated. So far i haven't had any problems with the new release except for this annoyance.

Dell xps 15
4 core I-7 2.0 ghz processor
nvidia w/ optimus
ubuntu 12.04 installed

---

### Post by Mr Nemo on 2012-04-28
bump

---

### Post by mike555 on 2012-04-28
I would suggest complete uninstall of gnome shell and cinnamon,from unity, then use cinnamon "stable" ppa and install cinnamon.

[http://is.gd/2nat9G](http://is.gd/2nat9G)

---

### Post by Mr Nemo on 2012-04-29
So removing and reinstalling cinnamon/gnome shell didnt work, but I did fix the issue. Removing nvidia-current fixed the problem; Cinnamon works beautifully. The problem now is that Unity 3D defaults to Unity 2D. Is there some way to install nvidia current but have it load only when Unity 3D is selected?

---

