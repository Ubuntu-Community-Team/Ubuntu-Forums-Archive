---
title: "Deleted files but did not clear storage space"
date: 2010-04-02
forum: General Help
---

### Post by rmedved on 2010-04-02
Yesterday I deleted about 50GBs worth of space from home folder then emptied the trash. However, this did not clear up any free space on my hard drive. I remember now that the files were locked but I don't remember having any problem simply deleting them. They aren't showing up in there original folder nor are they showing up in the trash. I need my 50GBs... what's going on here?

Thank you,
Robbie

---

### Post by rmedved on 2010-04-02
Another note, i just ran disk usage analyzer.. it says I have a capacity of 100GBs and roughly 10GBs of free space but when it scans my filesystem it says that i'm only taking up around 30GBs.

---

### Post by colorlessprism on 2010-04-02
i noticed once that i was slowly losing space. first i check the "trash" and found a ton of stuff in there. i emptied the trash but still wasn't where i wanted to be space wise. then i found "bleachbit" i ran it as root, checked the apt-get boxes, and clicked delete. after that i went into synaptic and under status there is a filter that says something to the effect of "residual config". i highlighted everything and check "completely remove", after that i clicked apply...i recovered a ton of space after doing these things...

---

### Post by Shazaam on 2010-04-02
There is also a Trash folder in root...
root/.local/share/Trash
To access it enter this in terminal (WARNING! Be very careful as this code gives you ROOT access to EVERYTHING and you can easily trash your system by deleting/editing the wrong folders/files)...
```
gksudo nautilus
```
One caveat- If you right-click something in root's Trash/files and Trash/info folders then click "Move to Trash" nautilus will make a copy of what you just deleted in the same folders. Highlight the offending stuff, hold down the shift key, then hit the Delete key on your keyboard to PERMANENTLY remove them.

---

### Post by rmedved on 2010-04-04
thanks shazaam that did the trick

---

