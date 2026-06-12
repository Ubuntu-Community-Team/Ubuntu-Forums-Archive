---
title: "how do i move window buttons back to left side?"
date: 2012-01-25
forum: General Help
---

### Post by rajohns08 on 2012-01-25
for some reason i can't get them to go back to the left side. i am supposed to edit button_layout in metacity correct? to 'close,minimize,maximize:menu'?

i am in 11.10. if i log into gnome classic they are on left side. but when i log into new gnome they are on right side

---

### Post by cottfcfan on 2012-01-25
The easiest way i have found is to install ubuntu tweak.
```
sudo add-apt-repository ppa:tualatrix/ppa
```
```
sudo apt-get update && sudo apt-get install ubuntu-tweak
```
Then go to tweaks/window manager settings.
This works for Ubuntu, but ive never tried it in gnome-shell.
It's easy enough to reverse though.

---

### Post by rajohns08 on 2012-01-25
> **cottfcfan said:**
> The easiest way i have found is to install ubuntu tweak.
```
sudo add-apt-repository ppa:tualatrix/ppa
```
```
sudo apt-get update && sudo apt-get install ubuntu-tweak
```
Then go to tweaks/window manager settings.
This works for Ubuntu, but ive never tried it in gnome-shell.
It's easy enough to reverse though.

thanks this worked after a logout

---

