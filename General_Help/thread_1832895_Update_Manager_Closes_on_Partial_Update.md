---
title: "Update Manager Closes on Partial Update"
date: 2011-08-25
forum: General Help
---

### Post by ambdeep on 2011-08-25
If I use the GUI for partial update, the update manager automatically shuts down as soon as I enter my password. I have tried reinstalling my update manager but it doesnt make any difference. Please help.

---

### Post by dino99 on 2011-08-25
into a terminal, clean the system first:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade 

sudo dpkg --configure -a

and note that "partial" means "incomplete", so you better have to wait for the missing update dependencies (otherwise: breakage ahead ;))

---

