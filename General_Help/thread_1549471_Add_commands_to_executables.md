---
title: "Add commands to executables?"
date: 2010-08-09
forum: General Help
---

### Post by dek8 on 2010-08-09
How do i add commands to excecutables?

Running a minimalist install of ubuntu running xfce.

I want for example "--no-existing-session" under totem, where do i add it? how?

---

### Post by kerry_s on 2010-08-09
/usr/share/applications/totem.desktop

make yourself a right click action for easy root editing:

gksudo mousepad %f

next tab click txt & other

---

### Post by dek8 on 2010-08-09
im looking but there is no totem.desktop file in /usr/share/applications/ here... ?

im using pcmanfm so i get root access in the file manager, and gedit for text editing...

---

### Post by kerry_s on 2010-08-09
> **dek8 said:**
> im looking but there is no totem.desktop file in /usr/share/applications/ here... ?

im using pcmanfm so i get root access in the file manager, and gedit for text editing...

sorry, when looking in the file manager the name of the program is shown, just edit the 1 that says "Movie Player" with your editor, you'll see the name.

---

### Post by dek8 on 2010-08-10
Ty.

---

### Post by dek8 on 2010-08-14
i reinstalled linux and tried this again without any luck. are there any other places i need to check for it to work?

Edit; Had to reboot.

---

