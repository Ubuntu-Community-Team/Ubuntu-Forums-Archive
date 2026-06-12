---
title: "remove deluge"
date: 2012-03-25
forum: General Help
---

### Post by berryboy on 2012-03-25
hello there,

i have some issues with deluge and want to remove it, but when i apt-get remove deluge. it is not found :( how can i remove this manually? 

thanks Berryboy

---

### Post by berryboy on 2012-03-26
i've not gotten any further with this :( any help please dont want to have to keep formatting every time i want to uninstall a program :(

---

### Post by Vaphell on 2012-03-26
```
dpkg --get-selections | grep deluge
``` will show you installed packages with deluge in their names

---

