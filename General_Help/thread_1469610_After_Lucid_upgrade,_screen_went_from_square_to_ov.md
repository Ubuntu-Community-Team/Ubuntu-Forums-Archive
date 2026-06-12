---
title: "After Lucid upgrade, screen went from square to ovalish"
date: 2010-05-02
forum: General Help
---

### Post by TheWanderingMaverick on 2010-05-02
After I upgraded from 9.10 to 10.04, my monitor was fine. Then, after a day, when set at 1024 X 768 the screen is distorted so the sides of the desktop are very curved. What's going on?

---

### Post by dino99 on 2010-05-02
sudo rm -f /etc/X11/xorg.conf

sudo dpkg --configure -a

goto system --> admin --> hardware driver

is yours activated ?

which graphic card and which driver installed ?

---

