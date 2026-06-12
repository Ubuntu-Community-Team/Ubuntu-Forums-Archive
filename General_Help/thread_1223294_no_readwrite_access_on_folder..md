---
title: "no read/write access on folder."
date: 2009-07-26
forum: General Help
---

### Post by bubblez-gopop on 2009-07-26
Heya, was mucking around today and made a new folder and was playing around with its properties. I set its permissions to none, for the owner, me. Now i have a random 'new folder' in my home folder that i can do nothing with. Can someone tell me how to get rid of it lol and also one more problem. I installed xfce and removed gnome and kde everything still working fine and all my apps still go but i have no app for User and Group modification, any ideas?

---

### Post by SKeaLoT on 2009-07-26
about the folder, try
```

$ chmod +rw 'New Folder'

```

that should give it Read and Write privileges

about the users dialog... i'm not sure, but i think xfce uses the gnome users dialog for that purpose.. could be wrong though

---

### Post by bubblez-gopop on 2009-07-26
thanks skealot, that did the trick. is there any way to get the gnome user dialog back?

---

### Post by bubblez-gopop on 2009-07-26
2nd problem solved, i installed kuser from synaptic package manager. its working fine.

---

### Post by SKeaLoT on 2009-07-26
the command for the user and group management is
```

user-admin

```
try running it on a console to see if you still have it installed

---

