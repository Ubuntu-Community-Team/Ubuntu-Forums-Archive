---
title: "Gnome Terminal History"
date: 2006-06-19
forum: General Help
---

### Post by vvlist on 2006-06-19
Okay, I thought I would further secure my laptop by removing the Gnome Terminal History function with a quick > rm -f $HOME/.bash_history
touch $HOME/.bash_history
chmod 000 $HOME/.bash_history However, I would like to to get this useful function back, does anyone know to reverse what I did and get the Gnome Terminal History function back? Your help would be greatly appreciated, thanks.

---

### Post by ayoli on 2006-06-19
rm -f .bash_history , then a new.bash_history should be created, i guess

---

### Post by vvlist on 2006-06-19
[QUOTE=ayoli]rm -f .bash_history , then a new.bash_history should be created, i guess[/QUOTE]
Thanks for that, I'm still a little scared of that rm command. O:) But it worked, and I'm grateful.

---

