---
title: "Daul boot problem"
date: 2010-05-07
forum: General Help
---

### Post by smile-its-smiley on 2010-05-07
I've just installed 10.04 and its the best distribution i've seen yet! But I can no longer switch between windows and ubuntu like I have in previous installs. I get the normal boot screen options which are something along the lines off.

Boot ubuntu 10.04
recover ubuntu 10.04
restore factory default settings of your Toshiba machine

but no option to boot into windows, I can still access all my files and settings from within Ubuntu, so i haven't overwritten Windows

---

### Post by ajgreeny on 2010-05-07
Try ```
sudo update-grub
```which may find your windows install and add it to grub.

---

