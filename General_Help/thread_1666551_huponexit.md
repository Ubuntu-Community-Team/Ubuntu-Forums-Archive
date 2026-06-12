---
title: "huponexit"
date: 2011-01-13
forum: General Help
---

### Post by HeroesDieYoung on 2011-01-13
I have a program that gets launched by a script and runs in the background.  I need for that program to exit when the executing user logs out.

I found that if huponexit is set with shopt, that the program will receive the HUP signal and I can catch that and exit.  However, that option is not set by default.

It works fine if I do `shopt -s huponexit` by hand from the command line, but I have tried adding that line to the script before launching the executable, and tried adding that line to my .profile file, but was not successful in either case.

What is the method for setting huponexit ??

EDIT: I added `shopt -s huponexit` to the end of .bashrc as well, so that it would be executed for every shell instance.  However, my program still did NOT receive a SIGHUP when I logged out.  So far I have only made it receive a SIGHUP if I manually set huponexit and then manually start the program in the background.

---

### Post by HeroesDieYoung on 2011-01-14
Surely there is a standard way to make shell options set with 'shopt' persistent?  Someone must have the answer???

---

### Post by HeroesDieYoung on 2011-01-14
Surely there is a standard way to make shell options set with 'shopt' persistent?  Someone must have the answer???

---

### Post by HeroesDieYoung on 2011-01-14
Surely there is a standard way to make shell options set with 'shopt' persistent?  Someone must have the answer???

---

