---
title: "Ubuntu 9.10 to 10.04 upgrade problem"
date: 2010-05-07
forum: General Help
---

### Post by babltiga on 2010-05-07
I was upgrading ubuntu 9.10(64 bit) to 10.04 by Update Manager, first 3 steps were ok but when installing downloaded packages I was asked for proxy server/port for "ttf-mscorefonts-installer" when I hit enter at 'OK' something went wrong and the steps "Cleaning up" and "Restarting the computer" were skiped (the window closed automatically), so I did restart manually, now ubuntu 10.04 starts fine and all installed packages are updated, so my question is how to check if old/unused packages were removed and if the system is ok ...

---

### Post by dino99 on 2010-05-07
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by babltiga on 2010-05-07
Thanks, I think ```
sudo apt-get autoremove
``` helped me.

---

