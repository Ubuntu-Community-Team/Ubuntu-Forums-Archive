---
title: "Ubunto 10.04 stuck on splash screen"
date: 2010-11-17
forum: General Help
---

### Post by anthrop2 on 2010-11-17
I removed Cairo from synaptic. Since then Ubuntu doesn't start - it gets stuck on the splash screen, which is Mac-like (since I had installed Macubuntu): I see the apple logo and the rotating wait  prompt is running like hell.
My pc has dual boot (Vista is my other OS) with grub2 loader.
Please help!:confused:

---

### Post by sikander3786 on 2010-11-17
Select recovery mode from Grub menu, 2nd on the list and you'll see an option to reconfigure packages or fix broken packages or something like that. Try that and reboot.

---

### Post by anthrop2 on 2010-11-18
Tried that but it didn't help.
Also switched to cmd line and run > sudo apt-get install gnome-core.
No luck either.
Any other idea?
Thanks.

---

### Post by sikander3786 on 2010-11-18
Try

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

