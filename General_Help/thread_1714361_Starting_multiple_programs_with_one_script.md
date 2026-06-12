---
title: "Starting multiple programs with one script"
date: 2011-03-25
forum: General Help
---

### Post by Theobalt on 2011-03-25
Hi!

I want to write a script that launches a set of programs I need for such or such particular task. For example, I wrote this one:

# -*- coding: utf-8 -*-
nautilus /mnt/scratch/legeron/levesqu2
filezilla
gnome-terminal
gedit

But gnome-terminal will not start until I close filezilla, and gedit until I close gnome-terminal. How can I get the whole set to start up?

Thanks!

---

### Post by Smart Viking on 2011-03-25
Like this
```
# -*- coding: utf-8 -*-
nautilus /mnt/scratch/legeron/levesqu2 &
filezilla &
gnome-terminal &
gedit
```

---

### Post by blind2314 on 2011-03-25
Add a & behind them to background the process, and return control to the shell.
 
```
filezilla &
blahprogarm &
```
 
etc.
 
 
EDIT:
 
DANGIT! You beat me, viking :(

---

### Post by Theobalt on 2011-03-25
Nice! Thanks!

---

