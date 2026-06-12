---
title: "Reinstall Gnome?"
date: 2006-02-19
forum: General Help
---

### Post by SirKillalot on 2006-02-19
Hi,
I have problems with gnome for some weeks now: everytime I start gnome the gnome-panel appears and disappears all the time. No desktop gets initialized or something else, everything that happens is that the panel comes and goes away all the time. I even can't find the reason for that. To have at least a GUI I installed kubuntu-desktop (I _HATE_ kde). Now I ask you if I can either reinstall gnome from scratch (and delete all config files obviously) or start it so that I can read at least an error message. "startx" doesnt start gnome but enlightenment, so I can't get any error messages. I hope I can use gnome some day again.
Thanks

---

### Post by newuser111 on 2006-02-19
try 

sudo rm ~/.ICEauthority

sudo rm ~/.gconf

sudo rm ~/.gnome

sudo rm ~/.gnome2

sudo rm ~/.metacity

sudo rm ~/.nautilus

sudo rm ~/.Xauthority

that should get rid of all the temp config files

---

