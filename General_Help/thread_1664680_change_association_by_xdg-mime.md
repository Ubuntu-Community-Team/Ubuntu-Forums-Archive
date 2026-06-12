---
title: "change association by xdg-mime"
date: 2011-01-11
forum: General Help
---

### Post by alexxxm on 2011-01-11
Hi people,
I am trying to change the current association for MS word documents from Kword to openoffice.
I guess I'm following closely the indicated step in the manual, i.e.:

~ xdg-mime default openoffice.org-writer.desktop application/msword

but when I check it I get this:
~ xdg-mime query default application/msword
kword.desktop


what am I doing wrong?

thank you...

alessandro

---

### Post by alexxxm on 2011-01-12
The perfect solution has been given to my - simply bypass xdg-mime (if you're using KDE) and use this:

~ keditfiletype application/msword

simple&painless!


alessandro

---

