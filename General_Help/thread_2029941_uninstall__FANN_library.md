---
title: "uninstall  FANN library"
date: 2012-07-20
forum: General Help
---

### Post by fire planet on 2012-07-20
i used CMAKE to install FANN library via it . after CMAKE installated, i used below commands to install FANN :
```
cmake .
sudo make install 

```

now FANN has installed in  "usr/local". but i countered a problem with this library and want to remove it safely .
how should i uninstall it?

---

### Post by dino99 on 2012-07-20
try :

sudo apt-get purge FANN

or :

sudo rm /usr/local/FANN

note: write the exact package name (lowercase is not uppercase)
note2: you can use nautilus to browse /usr/local folder to check this package

---

### Post by Pand5461 on 2012-07-20
Also ```
 sudo make uninstall 
``` in the source directory.

---

