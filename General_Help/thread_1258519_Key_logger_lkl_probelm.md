---
title: "Key logger lkl probelm"
date: 2009-09-05
forum: General Help
---

### Post by colomob on 2009-09-05
i finish installing it but when am going to run the comand to start this appears:

```
 Started to log port 0x60. Keymap is /usr/share/lkl/keymaps/us_km. The logfile is /home/Document/System/log.
fopen(): No such file or directory 
```

is it an error?? and if it si why is it?

---

### Post by Liolikas on 2009-09-05
Maybe you installed not from "normal" ways. This error means program lacks other things, packages. Read REAME for more info.

As most basic example Fifefox use gtk for window drawing, without gtk FF start will fail. Generally Synaptic/apt-get fix these things automatically, but if you use other ways to install program you have to deal with this yourself too.

---

### Post by colomob on 2009-09-05
how would i know what is missing? i read the README file but it dosent say anything help full

---

### Post by colomob on 2009-09-05
Am sorry am still kinda new to ubuntu. it might not be a good excuse but i been trying hard to solve evrything by myself. but i dont know what to do anymore with this. i have search for similar cases everywere but i cant seem to find the answer. other cases havent even made it this far. if you need any extra info let me know.

---

### Post by 3rdalbum on 2009-09-05
```
fopen(): No such file or directory
```

A file it wants to open does not exist. The terminal output shows the locations of two files that it is trying to open, maybe check if they exist?

---

