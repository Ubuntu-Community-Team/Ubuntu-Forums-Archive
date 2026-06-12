---
title: "half of log in screen black"
date: 2011-09-30
forum: General Help
---

### Post by n.foster on 2011-09-30
as the title says, the right half of the screen is black with a large mouse pointer, when I go to log in.when you move the pointer on to the black half, the large pointer moves aswell turning the area white!!  I can log in as usual, because I can still see half the user name, just interested to know if there is a fix?

---

### Post by Krytarik on 2011-09-30
Run this command to disable the magnifier feature of the login screen, I presume you unintendedly activated it there in the first place:
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```
Greetings.

---

### Post by n.foster on 2011-09-30
thanks, i'll try that later

---

### Post by n.foster on 2011-09-30
presumably i copy that to the terminal? which i have done, is it missing something as is doesn't do anything?

---

### Post by wildmanne39 on 2011-09-30
Hi, after you enter the command you need to enter your password and hit enter, and it will not show the password in the terminal, and the command will not show any output as long as there were no errors.
Thank you

---

### Post by n.foster on 2011-10-01
i get it, thanks !

---

### Post by n.foster on 2011-10-01
i get it, thanks !

---

