---
title: "Shell scripts"
date: 2010-03-05
forum: General Help
---

### Post by Mr Nemo on 2010-03-05
I'm making nonsense shell scripts for practice. Using a launcher connected to a script I want to open a terminal and run the script I wrote in that terminal. Is there anyway to do this. Google is of no help.

---

### Post by patchwork on 2010-03-05
Absolutely there is...put something like this in the launcher
xterm -e <launch command>

or gnome-terminal -e <launch command>

If you get an error stating that a child process could not be created with gnome-terminal, you can try

gnome-terminal -x <launch command>


the man pages for gnome-terminal and xterm list all of the available options to be run, if you want to control things like window geometry, profile, tabs, etc.

---

### Post by Mr Nemo on 2010-03-05
Nice, that worked well. I didn't even think of putting it in the launcher like that, I was trying to put it directly in the script. Thanks.

---

