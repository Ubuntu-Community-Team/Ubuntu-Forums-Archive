---
title: "Run .exe in 2 cores"
date: 2010-08-24
forum: General Help
---

### Post by JCM_Pico on 2010-08-24
Hi there,
I have an .exe program to do some routines in Linux and it works based in Fortran.  When I run the .exe, simply typing ./filename.exe it only uses 50% of my 2 core cpu..
Is it possible to make it use 100%, the 2 cores, since it takes a lot off time to do all the work?

---

### Post by Vaphell on 2010-08-24
is that app multithreaded and does it utilize more than 1 core in a multicore windows environment?

---

### Post by JCM_Pico on 2010-08-24
I never used it in windows.... and I don't know if it is multithreaded.... probably it isn't...

Thank you any way

---

### Post by davidmohammed on 2010-08-24
you've answered your own question - if the program isnt multithreaded, then multiple cores will not help you.  You'll need to recompile the application with some threading compiler options at a guess.

---

### Post by JCM_Pico on 2010-08-24
Recompiling nice idea, I will give it a try

Thank you all

---

