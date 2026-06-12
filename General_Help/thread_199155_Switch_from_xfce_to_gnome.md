---
title: "Switch from xfce to gnome"
date: 2006-06-18
forum: General Help
---

### Post by waltervalderrama on 2006-06-18
Hi, how can i switch my desktop session from xfce to gnome from a terminal. I know that theres is a command in fedora "switchdesktop gnome". Does it exist in ubuntu?

:roll: :roll:

---

### Post by xXx 0wn3d xXx on 2006-06-18
If you have gnome installed (sudo apt-get install ubuntu-desktop if not) then go under System > Quit > Logout and then click session and select "Gnome" and then login. You should be back on Gnome.

---

### Post by aysiu on 2006-06-18
I would advise using *aptitude* instead of *apt-get*: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` There's no command to switch. You have to log out, select the "Gnome" session, and then log back in again.

---

### Post by adam_benson on 2008-01-22
I'm trying both suggestions and I'm still looking at Xfce when the machine starts. I also notice I do not have the option to select a session when I begin. How do I make that selection?
thanks in advance,
Adam

---

### Post by silviur on 2008-01-22
Search for something like "Login window" in the Administration menu (in Gnome), or for something similar in xfce, and disable "automatic login" for your user. Then restart X, and a login window will appear, click Sessions and choose Gnome.

---

### Post by adam_benson on 2008-01-22
The Automatic login is clear (not selected) I am also not seeing a dialog for selecting a session when I log back in or reboot. Any suggestions as to where to go from here?
-Adam

---

### Post by silviur on 2008-01-22
You can select the session on the screen that you are looking to obtain. It's strange you have automatic login disabled. 
You need some guy who knows how to edit your initialisation files, this is over my head. 
Good luck!

---

