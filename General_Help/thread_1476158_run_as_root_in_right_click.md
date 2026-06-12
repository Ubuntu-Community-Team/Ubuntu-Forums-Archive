---
title: "run as root in right click"
date: 2010-05-07
forum: General Help
---

### Post by rock4christ on 2010-05-07
is there a way to add a 'run as root' command to the right click menu? so i could right click on a launcher, or a file in /usr/bin(or some other no editing folder) and easily run as root?

---

### Post by WorMzy on 2010-05-07
I believe nautilus-gksu is what you want. Just install it (sudo apt-get install nautilus-gksu), and see if it appears. You may need to restart gdm (or reboot your PC) to get it to show.

---

### Post by doas777 on 2010-05-07
you can also use nautilus-actions to create simple Rclick scripts for nautilus. since you get to specify the payload of the command/script you could always add gksu whatever command.

---

### Post by finlost on 2010-05-07
I am not sure if this is exactly what you want.

In Ubuntu Tweak, go to Manage Scripts.  Drag *Browse as root* to the *Nautilus-scripts* pane.

---

### Post by rock4christ on 2010-05-07
> **WorMzy said:**
> I believe nautilus-gksu is what you want. Just install it (sudo apt-get install nautilus-gksu), and see if it appears. You may need to restart gdm (or reboot your PC) to get it to show.

thanks! thats exactly what i want. was getting tired of having to alt+f2 gksudo nautilus just edit files w/o the terminal

---

### Post by Spagnum on 2011-08-31
nice... thanks!

---

