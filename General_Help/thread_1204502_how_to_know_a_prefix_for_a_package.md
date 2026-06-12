---
title: "how to know a prefix for a package"
date: 2009-07-04
forum: General Help
---

### Post by hero1900 on 2009-07-04
i am trying to install some plugins for thunar and when i try to figure the prefix by this command **pkg-config --variable prefix thunarx-1** i get nothing 
so what is the problem i am sure that i have thunar but is thunarx are diffrent or what??

---

### Post by hero1900 on 2009-07-06
bump
:mrgreen:

---

### Post by shae on 2009-07-06
I am not sure what you are trying to do because pkg-config is used for compiling programs.  What result are you trying to achieve?

---

### Post by hero1900 on 2009-07-13
what i was trying to do is to know where is the location of thunar installed

---

### Post by shae on 2009-07-14
are you sure you are not wanting to use
```
--prefix=/usr
```

---

### Post by mcduck on 2009-07-14
> **hero1900 said:**
> what i was trying to do is to know where is the location of thunar installed
```

whereis thunar
```
Or to just to find the executable:
```
which thunar
```

---

