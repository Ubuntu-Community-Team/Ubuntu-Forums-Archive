---
title: "Running programs from the desktop"
date: 2006-02-09
forum: General Help
---

### Post by Dko on 2006-02-09
I have a shortcut thingy on the desk top to a program (firestarter).  It keeps telling me I don't have permisions to run it.  I even tried chmoding it and trying the right click script thats in the starter guide. It just brings up a document that has weird text about the file.  any help

---

### Post by taurus on 2006-02-09
You may have to run it as 

sudo firestarter
 
instead of just "firestarter"...

---

### Post by aysiu on 2006-02-09
I believe Firestarter is a graphical application. Therefore, the desktop icon's command should be ```
gksudo firestarter
```

---

