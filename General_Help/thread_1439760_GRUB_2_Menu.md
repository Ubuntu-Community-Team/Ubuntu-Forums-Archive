---
title: "GRUB 2 Menu"
date: 2010-03-26
forum: General Help
---

### Post by Jlb181 on 2010-03-26
I would really like to get to the GRUB menu when I boot up my machine.  GRUB 1.5 had a timer, I could hit ESC if I needed the GRUB menu.  I can't seem to get a timer and I need it.  Does any body know the edit to the grub.cfg file I need?

Thanks

---

### Post by philinux on 2010-03-26
You need to edit

/etc/default/grub then run

```
sudo update-grub
```
Which regenerates /boot/grub/grub.cfg which is really a file you should not edit.

It's now the shift key and not esc. See link in my sig for grub2.

---

### Post by prodigy_ on 2010-03-26
```
sudo sed -i 's/GRUB_HIDDEN_TIMEOUT=.*/#&/' /etc/default/grub
sudo update-grub
```

---

### Post by ajgreeny on 2010-03-26
Also you hold down shift instead of Esc now to get the menu.  Grub2 has changed many of those sort of things.  Have a look at, and good read of:-
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

