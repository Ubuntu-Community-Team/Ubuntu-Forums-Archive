---
title: "Need to edit /etc/profile"
date: 2006-06-16
forum: General Help
---

### Post by FlyingPenguin on 2006-06-16
I need to add a line to /etc/profile so I can get this X-Plane sim to work. Problem is, I don't know how I can do that since it is read only and the owner is root. 

What should I do?

---

### Post by scxtt on 2006-06-16
is it your box, if so - sudo:


[indent]sudo vi /etc/profile[/indent]


then do a :wq! to save it and exit from vi ...

---

