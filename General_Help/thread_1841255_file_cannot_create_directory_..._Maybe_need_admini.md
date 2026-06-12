---
title: "file cannot create directory ... Maybe need administrative privileges"
date: 2011-09-09
forum: General Help
---

### Post by aria john on 2011-09-09
Hi ,
I was installing a software , and it was fine until I wrote the command
#
make install

where I got the following error:

#
CMake Error at cmake_install.cmake:36 (FILE):
file cannot create directory: /usr/local/include/player-3.0. Maybe need administrative privileges.

----
Any ideas how to solve this problem ?

---

### Post by raja.genupula on 2011-09-09
```
sudo make install 
```
give your password 
its gonna be fine

---

### Post by aria john on 2011-09-09
You are right (:

Thank you so much (:

---

### Post by raja.genupula on 2011-09-09
not only this time , everytime if your dealing with filesystem dir then you must be root . 
so please remember this case for future purpose also .

---

### Post by sisco311 on 2011-09-09
> **raja.genupula said:**
> ```
sudo make install 
```
give your password 
its gonna be fine

Or:
```
sudo checkinstall
``` ;)

[uhelp]community/CheckInstall[/uhelp]

---

### Post by raja.genupula on 2011-09-10
thanks i will remember this also .

---

