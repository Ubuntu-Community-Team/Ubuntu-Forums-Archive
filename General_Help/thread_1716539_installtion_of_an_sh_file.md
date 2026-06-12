---
title: "installtion of an sh file"
date: 2011-03-28
forum: General Help
---

### Post by Kaspar44 on 2011-03-28
Hi i installed an sh file with the command sudo sh it installs fine i go to run it the opening image comes up but then nothing happens and comes up with this error in the terminal screen /usr/lib/gtk-2.0/2.10.0Aborted  any ideas?

---

### Post by doas777 on 2011-03-28
looks like the code requires some missing dependencies

check where you got the code first, and if nothing else you could try installing gir1.0-gtk-2.0, though I have no idea if that is desirable or not

```
Lucid:~$ apt-cache search gtk-2.0
gir1.0-gtk-2.0 - The GTK+ graphical user interface library

```

---

