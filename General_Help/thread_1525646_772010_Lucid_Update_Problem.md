---
title: "7/7/2010 Lucid Update Problem"
date: 2010-07-07
forum: General Help
---

### Post by 4gsl on 2010-07-07
I ran Update Manager for the 7/7/2010 update then rebooted. Since then, my screen went blank twice (gray then black--had to reboot both times), and my browser (FireFox) arbitrarily closes while I'm using it. Anyone know what's up? Thanks!

---

### Post by mörgæs on 2010-07-07
I can not give you an exact solution, but in general I would wait a day or two and then run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

If something was wrong in the update, there is a good chance that a fix is already in the making.

---

### Post by nothingspecial on 2010-07-07
If you got a new kernel try booting into an earlier one at the grub screen.

---

