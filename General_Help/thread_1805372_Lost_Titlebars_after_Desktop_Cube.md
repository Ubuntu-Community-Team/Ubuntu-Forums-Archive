---
title: "Lost Titlebars after Desktop Cube"
date: 2011-07-15
forum: General Help
---

### Post by ubunt2guy on 2011-07-15
After I enabled desktop cube the titlebars all disappeared.  

I tried reverting back but that didn't work.

Anyone know how to get them back?

Using Ubuntu 11.04 with Gnome (not Unity) 

Thanks

---

### Post by wildmanne39 on 2011-07-16
> **ubunt2guy said:**
> After I enabled desktop cube the titlebars all disappeared.  

I tried reverting back but that didn't work.

Anyone know how to get them back?

Using Ubuntu 11.04 with Gnome (not Unity) 

ThanksHi, this should reset compiz.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```

---

### Post by ubunt2guy on 2011-07-16
Worked.

Thank you so much.

---

### Post by wildmanne39 on 2011-07-17
> **ubunt2guy said:**
> Worked.

Thank you so much.Hi, your welcome! 
would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

Also here is a guide for setting up the cube in natty.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

