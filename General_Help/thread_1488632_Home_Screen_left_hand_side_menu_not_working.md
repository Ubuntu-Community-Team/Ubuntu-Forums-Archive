---
title: "Home Screen left hand side menu not working"
date: 2010-05-20
forum: General Help
---

### Post by Roshelle on 2010-05-20
Good day I have ubuntu 10.04 on the home screen page in the left have colum you have a list of menu items when you install ubuntu, I happen to deselect one of teh menu items. I now cannot reinstate the menus I have included a screen-shot of the home screen so you can see the menu items I have available on the left hand side.

Any assistance would be appreciated

---

### Post by blazemore on 2010-05-20
Hit alt+f2 and type "alacarte" (without the quotes) and press Enter.
IIRC, that's the name of the menu editor.

---

### Post by dino99 on 2010-05-20
into a console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure software-center
sudo dpkg --configure -a

---

### Post by Roshelle on 2010-05-20
[blazemore]("http://ubuntuforums.org/member.php?u=326352") thank you thank you

---

### Post by blazemore on 2010-05-20
> **dino99 said:**
> into a console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure software-center
sudo dpkg --configure -a

That would work but would be overkill

---

