---
title: "My selections are blank   ???"
date: 2010-06-26
forum: General Help
---

### Post by KingArthur72076 on 2010-06-26
When I go to appearances and the box opens...theres nothing there. I try to open calculator and its blank. I can't even take a screen shot because it is also blank.

Since I can't see what I'm working on, how can I reset the appearance to get it fixed without reloading my computer?

---

### Post by dino99 on 2010-06-26
into a console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure gnome-color-chooser

---

### Post by KingArthur72076 on 2010-06-26
Thanks...I'm giving it a try now.

---

