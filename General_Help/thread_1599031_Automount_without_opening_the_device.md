---
title: "Automount without opening the device"
date: 2010-10-17
forum: General Help
---

### Post by Square87 on 2010-10-17
Hello
I have kubuntu 10.10 when i insert a pen drive, i cannot navigate in the dirs from a shell, but i have to open dolphin before and then i have to click on the /media/$newdir and then i can navigate... is there a way to automount without opening dolphin?
Thanks

---

### Post by Toz on 2010-10-17
Have you tried installing usbmount?

> sudo apt-get install usbmount

I don't run kubuntu, but this has worked for me in the past with ubuntu.

---

### Post by Square87 on 2010-10-17
Thank you
I tried usbmount and pmount but both create a dire in /media/.. and i need the sudo command to remove that dirs... is there a way to remove dirs in /media without have the root permission when i umount the device?

UPDATE:
There is pumount, that remove also the dir, but if i remove the device without pumount the /media/$dir is not removed anymore. Usbmount returns read permission only.

---

