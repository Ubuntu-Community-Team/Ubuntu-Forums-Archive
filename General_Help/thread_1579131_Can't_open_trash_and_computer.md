---
title: "Can't open trash and computer"
date: 2010-09-21
forum: General Help
---

### Post by rocker9455 on 2010-09-21
When i try to open the trash can in nautilus i get this message:
"Sorry, could not display all the contents of "trash": Operation not supported"
Also when i click on the computer icon on docky nothing happens.
When i plug my ipod in, it mounts but it doesnt appear in rhythmbox (I assume another related problem) Any idea how i can remedy this problem?

---

### Post by rocker9455 on 2010-09-23
Bump. Anyone? It also seems as if i cant open links from empathy. Looks like my symlinks are screwed... any ideas on how to remedy this?

---

### Post by 7h3d4rk0n3 on 2010-09-23
I also have the same problem. It happens with Computer, Trash, and Network. I believe it to be a problem with gvfs, but am not sure how to fix it. Seemed to happen after I did an update.

---

### Post by Todamont on 2012-05-13
bump. I have this error now after a gtk+ update.

---

### Post by krytorii on 2012-05-13
try:

```
sudo apt-get purge nautilus
sudo apt-get autoremove
sudo apt-get install nautilus
```

---

