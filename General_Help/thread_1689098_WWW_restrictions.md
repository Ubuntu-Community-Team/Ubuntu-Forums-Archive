---
title: "WWW restrictions"
date: 2011-02-16
forum: General Help
---

### Post by samishal on 2011-02-16
Hi guys 

after nearly 2 days without sleep and many many MANY energy drinks i have finally installed LAMP yay!

but it would appear that i cannot acccess my web sites becuase of the permisions on the www file, is there a a way to permanently remove them?

sam

---

### Post by t0p on 2011-02-16
To change the permissions for the *www* file, you can hit **Alt+F2**, type into the box that appears

```
gksudo nautilus /var/www
```

(or wherever it is the *www* file is located), then right-click on *www* and select Properties.  Then you can change the permissions to however you want them.

Just remember: once you've finished messing with the properties, close that Nautilus (File Manager) window, as anything you do in it is executed as root and you can inadvertently b0rk your system if you aren't careful.

---

### Post by samishal on 2011-02-16
cool thank buddy worked a trick however, now i can acces my files but when i try to open a .php one firefox asks me what to do with it rather than just opening the webpage??

ty v.much for help:popcorn:

---

### Post by samishal on 2011-02-16
also i put my website folder in the var/www folder but it does not appear on the index of page :S

---

