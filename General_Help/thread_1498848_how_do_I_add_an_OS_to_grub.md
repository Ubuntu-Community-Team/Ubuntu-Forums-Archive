---
title: "how do I add an OS to grub"
date: 2010-06-01
forum: General Help
---

### Post by littleoak on 2010-06-01
I have just made a clean install of ubuntu 10.4 on a  empty HDD. now I want to install windows on a second HDD. How do I modify Grub and get it to display. any advice will be appriciated.:popcorn:

---

### Post by drs305 on 2010-06-01
Install your Windows OS. Once you have, you may have to reinstall Grub2. Here is a link on how to fix that possibility:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

Once Grub2 is working, running the following command should run a search, find Windows, and automatically add it to the Grub2 menu.
```
sudo update-grub
```

---

### Post by dino99 on 2010-06-01
with multiboot, grub2 deals with other OS after running:

sudo grub-mkconfig
sudo update-grub

more info following the link below

---

