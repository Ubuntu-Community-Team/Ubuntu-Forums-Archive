---
title: "Control + Alt + Backspace does not restart X"
date: 2006-03-09
forum: General Help
---

### Post by akniss on 2006-03-09
When I used to hit CTRL + ALT + BACKSPACE, it would just restart X, like I presume it is supposed to.  A while ago (I think about the same time I installed XFCE) ctrl alt bkspc started taking me to a command line login.  I have to login, then when I  type startx, it would take me to XFCE.  I did some tinkering, and got startx to take me to gnome, but my theme is different.  The way I did this was by creating a file called .xinitrc in my home directory with the text gnome-session as the only content.  If I login after the ctrl+alt+backspace and type 
```
sudo /etc/init.d/gdm restart
```
then it will take me to the gdm graphical login screen.  How do I get ctrl+alt+backspace just to restart X like it is 'supposed' to?

---

### Post by BobSongs on 2006-03-10
Sorry. Never post when you're tired.

---

