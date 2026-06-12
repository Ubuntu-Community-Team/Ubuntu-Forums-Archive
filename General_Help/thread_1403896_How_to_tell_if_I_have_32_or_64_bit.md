---
title: "How to tell if I have 32 or 64 bit"
date: 2010-02-10
forum: General Help
---

### Post by miggerish on 2010-02-10
How do I tell which one I have?

32 or 64 bit?

seems simple, but I cant figure it out.

---

### Post by Megafag on 2010-02-10
> **miggerish said:**
> How do I tell which one I have?

32 or 64 bit?

seems simple, but I cant figure it out.

Chances are you have a 32 bit system. how did you get ubuntu?

---

### Post by NightwishFan on 2010-02-10
If you machine was made anytime in the last 3 years, and is not a netbook, It is probably a 64-bit system.

As for Ubuntu, if you do not know then you have 32-bit.

---

### Post by miggerish on 2010-02-10
> **NightwishFan said:**
> If you machine was made anytime in the last 3 years, and is not a netbook, It is probably a 64-bit system.

As for Ubuntu, if you do not know then you have 32-bit.

Wow, but there is no easy way to pull up some info and check for sure?

---

### Post by NightwishFan on 2010-02-10
What are you using? Windows or Ubuntu? On Ubuntu just run this in a terminal:
```
uname -a
```

If it says x86_64 its 64bit OS, I forget how to tell if your hardware is 64-bit.

EDIT: Try:
```
lshw -C cpu | grep width
```

---

