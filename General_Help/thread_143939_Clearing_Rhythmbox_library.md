---
title: "Clearing Rhythmbox library"
date: 2006-03-13
forum: General Help
---

### Post by rikard_grankvist on 2006-03-13
How can I clear the rhythmbox library completely from entries, and set up a new library path? When I first configured rhythmbox, I chose a library path that I later had to move. Now all the entries in the library point to a faulty path. Where can I change the library path, and remove the bad entries? Making a complete removal with synaptic doesn't work, it somehow remembers the library after I reinstall.

---

### Post by irw on 2006-06-28
Bump

I have the same question

---

### Post by doclivingston on 2006-06-28
Try going to "~/.gnome2/rhythmbox/" and deleting the file "rhythmdb.xml".

---

### Post by aysiu on 2006-06-28
I think doclivingston's on the right track. I'd try these commands: ```
mv ~/.gconf/apps/rhythmbox ~/.gconf/apps/rhythmbox.old
mv ~/.gnome2/rhythmbox ~/.gnome2/rhythmbox.old
```

---

