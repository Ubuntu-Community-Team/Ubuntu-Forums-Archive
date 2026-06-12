---
title: "Gnome-terminal default working directory"
date: 2009-12-22
forum: General Help
---

### Post by drfreema on 2009-12-22
I just installed 'kubuntu-desktop' over a gnome install (Intrepid) and when I start the terminal (gnome-terminal) from the Kickoff Launcher, the initial working directory is ~/Documents.

How do I set the default starting location to my Home directory?

Thanks.

---

### Post by opticyclic on 2009-12-22
You could edit your /home/username/.bashrc file to have this at the end
```
cd /home/username/
```

---

### Post by drfreema on 2009-12-22
> **opticyclic said:**
> You could edit your /home/username/.bashrc file to have this at the end
```
cd /home/username/
```

Thanks.  That worked.

---

### Post by aktiwers on 2009-12-22
There are properbly more elegant ways to do this.. but if you edit your ~/.bashrc file:
```
gedit ~/.bashrc
```and at the very end add:
```
cd $home
```It might do the trick.

Or change $home to the path of your home (/home/username/).

Has your defualt home folder location also changed for everything else?

Edit: too slow :(

---

