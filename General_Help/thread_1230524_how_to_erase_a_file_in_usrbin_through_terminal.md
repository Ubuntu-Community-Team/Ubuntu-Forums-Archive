---
title: "how to erase a file in usr/bin through terminal?"
date: 2009-08-03
forum: General Help
---

### Post by Codix121 on 2009-08-03
I need to erase a file I made in the Usr/bin terminal, but when I right click
and select move to trash bin it won't let me,
anyway to do this through terminal?

---

### Post by credobyte on 2009-08-03
```
gksudo nautilus /usr/bin

```Use carefully ;)

---

### Post by oldos2er on 2009-08-03
> **Codix121 said:**
> I need to erase a file I made in the Usr/bin terminal, but when I right click
and select move to trash bin it won't let me,
anyway to do this through terminal?
```

 sudo rm /usr/bin/filename
``` This will bypass the trash bin, so be certain you're typing the command and filename correctly.

---

### Post by tjwoosta on 2009-08-03
> **credobyte said:**
> ```
gksudo nautilus /usr/bin

```Use carefully ;)


or 
```
gksu nautilus --no-desktop /usr/bin
```

this way nautilus wont re-draw your desktop with the root account wallpaper

---

