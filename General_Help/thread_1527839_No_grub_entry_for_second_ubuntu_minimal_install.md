---
title: "No grub entry for second ubuntu minimal install"
date: 2010-07-09
forum: General Help
---

### Post by pbolle on 2010-07-09
okay so i did a minimal install beside my current ubuntu 10.04 install
everything went fine, i restarted went to grub and there was no option for my second ubuntu install.
i go into my normal ubuntu and see the 78 gb partition and all the files..

what could be the problem?

---

### Post by Woody1987 on 2010-07-09
in a terminal enter: sudo update-grub. This should add it. Restart and it should be there.

---

### Post by elliotn on 2010-07-09
```
sudo update-grub
```
Try that and see if it finds your new minimal

---

### Post by pbolle on 2010-07-09
i think it worked, but how do i get to the grub menu? it seems like it just passes by now?

---

### Post by Darkness Des on 2010-07-09
Press Shift while it's loading.

---

