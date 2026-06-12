---
title: "Can not enter Console Mode!"
date: 2010-08-14
forum: General Help
---

### Post by kertez on 2010-08-14
My problem is that I am trying to install an Nvidia driver on ubuntu 10.04, and I can not access my console mode by pressing ctrl alt f2. When I press that keystroke my cursor will disappear till I press alt f7. Can anybody help?

---

### Post by kertez on 2010-08-14
please help!

---

### Post by wojox on 2010-08-14
What's wrong with the one from the repo's?

Did you ever do that little tweak where you edit 

```
gksudo gedit /etc/init.d/rc
```

and find the line CONCURRENCY=none and change it to:

```
CONCURRENCY=shell
```

Because I did and it put me in the same situation you are now.

---

