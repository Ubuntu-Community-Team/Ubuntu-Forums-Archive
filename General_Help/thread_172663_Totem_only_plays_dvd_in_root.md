---
title: "Totem only plays dvd in root"
date: 2006-05-09
forum: General Help
---

### Post by nevle on 2006-05-09
The only way I can play dvd's is by opening totem as root then starting the disc, otherwise i get an error saying another device is using the sound card and refuses to play. I assume that some permissions need changing but i don't know which to check/change, can anyone help please?](*,)

---

### Post by aysiu on 2006-05-09
It's possible there's some lingering program that's hijacking the sound server for your user... I don't know how to deal with that.

But it's also possible that, for some strange reason, your user doesn't belong to the appropriate groups.

If you're the first user created during installation, the command ```
groups
``` in the terminal should yield this output: ```
username adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```

---

### Post by nevle on 2006-05-09
yes, i'm in all those groups.:confused:

---

### Post by visvak on 2006-05-09
hey i had the exact same error. it dint go away. i had viruses in my Win part at the same time. so i did a complete format and reinstall.

---

