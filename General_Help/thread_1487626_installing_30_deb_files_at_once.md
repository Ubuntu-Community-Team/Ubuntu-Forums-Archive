---
title: "installing 30 deb files at once"
date: 2010-05-19
forum: General Help
---

### Post by elliotn on 2010-05-19
is there a way to install about 30 .deb files at once

can this code work if I cd to the folder ```
i *.deb 
``` dont worry about dependencies they are all in the folder

---

### Post by zvacet on 2010-05-19
Yes,cd to the folder and then 

```
sudo dpkg -i *deb
```

---

### Post by elliotn on 2010-05-19
thanx

---

