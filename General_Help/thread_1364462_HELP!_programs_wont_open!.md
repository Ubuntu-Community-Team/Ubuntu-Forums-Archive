---
title: "HELP! programs wont open!"
date: 2009-12-25
forum: General Help
---

### Post by phillychease on 2009-12-25
some programs like firefox, obviously, opens but some like pidgin, rhythmbox, the disc burner, and sound recorder wont open!

heres what pops out when i run from terminal.

```
phillychease@phillychease:~$ rhythmbox
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Error re-scanning registry , child terminated by signal
Run 'rhythmbox --help' to see a full list of available command line options.
phillychease@phillychease:~$ pidgin
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Illegal instruction

```

---

### Post by phillychease on 2009-12-25
nvm i got it.
i had kdenlive installed which was probably the conflict.

uninstall frei0r-plugins from Synaptic
and update libcv1, libhihgui1 and libcvaux1.

---

### Post by brousch on 2010-01-05
I had this same problem today. I had to remove openshot to make things work again.

---

