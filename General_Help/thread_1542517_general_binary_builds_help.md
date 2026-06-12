---
title: "general binary builds help"
date: 2010-07-30
forum: General Help
---

### Post by andthewicked on 2010-07-30
I was hoping someone could help me with general make builds if you downlaod the source code for a program, examples such as oger, flight gear 2.0 and others. What do you have to do if you just download the .tar or .gz files to install them?

---

### Post by didac on 2010-08-05
First you extract the files, like right-clicking and 'Extract here' Then you compile it. 

First read the README and INSTALL files that usually accompany a tar package. They have specific instructions. Normally everything boils down to executing in a terminal:

```

./configure
make
sudo make install

```

If you have all the dependencies installed, you are through. If not, you'll get error messages which you have to interpret.

---

