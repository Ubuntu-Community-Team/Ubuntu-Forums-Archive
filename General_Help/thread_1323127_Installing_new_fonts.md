---
title: "Installing new fonts"
date: 2009-11-11
forum: General Help
---

### Post by wbjoly on 2009-11-11
I am trying to install new fonts.  I think I found the folder they are supposed to go in but I can not copy them there.  Supposed I am not the owner? and root is?

As far as I am aware there is only the one login, mine.  So how do I access the root so and change the permissions so I can add fonts

---

### Post by Somme on 2009-11-11
```
 
mkdir ~/.fonts
mv mynewfont.ttf ~/.fonts
fc-cache -f -v

```
 
No root privileges required.

---

