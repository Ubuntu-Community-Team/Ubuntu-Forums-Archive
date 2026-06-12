---
title: "after updating ubuntu 10.10 have lost winxp from the boot menu"
date: 2011-04-28
forum: General Help
---

### Post by inula on 2011-04-28
Hello everyone
              I installed ubuntu 10.10, dual boot with winxp then I ran the update manager and now I don't have the option to boot into windows, I have looked at other threads but none seem to answer my problem can anyone point me in the right direction?

---

### Post by Leppie on 2011-04-28
try the following command:
```
sudo update-grub
```

---

### Post by inula on 2011-04-28
I have tried that and it doesn't show windows at all in the list is there anyway to undo an update?

---

### Post by Finalfantasykid on 2011-04-28
Are you able to mount your windows partition in nautilus.

---

### Post by Leppie on 2011-04-28
there's not really a way of undoing an update.

could you download and run the boot info script and post the generated results.txt: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by inula on 2011-04-28
yes I can mount the windows partition and get into it for music and photo's etc when i need to but it gone from the boot menu.

---

