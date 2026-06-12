---
title: "C program to generate sound"
date: 2009-08-11
forum: General Help
---

### Post by nuke_fluke on 2009-08-11
in Turbo C/C++ compiler the header dos.h contains sound(int) function to generate sound of a particular frequency.

What is the equivalent header file to be included and function used in GCC in ubuntu linux?

Thanks

---

### Post by nuke_fluke on 2009-08-16
somebody please reply

---

### Post by credobyte on 2009-08-16
I think you are searching for something that simply does not exist ..
All you can do ( from what I know ) is to make a beep/bell:
```
printf("Beeep ... \n\a");
```

---

### Post by nuke_fluke on 2009-08-16
But since Unix is written using C, there must exist some function controlling the sound devices...

It looks logical to me that if my linux can play music of various frequencies, it should have such a function...

---

