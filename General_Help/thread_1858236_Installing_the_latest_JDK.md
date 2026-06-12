---
title: "Installing the latest JDK"
date: 2011-10-11
forum: General Help
---

### Post by Egregious on 2011-10-11
Hello, I'm new to Ubuntu, and I'm currently a college student in a Java Development Class.

I was wondering how to update my JDK from 1.6 to 1.7. I've downloaded the .rpm, but I'm not sure where to go from there.

Thanks for the help

-Egregious

---

### Post by Immolatus on 2011-10-11
you don't want the .rpm for use with Ubuntu. ".rpm " is for "redhat package manager". Ubuntu uses .deb files. I always go with the self extracting binary (works for both).

download the .bin and put it in a folder in your /home...extract.

Heres the fun part.....set the BASH path variable in .bashrc. I assume you know this all ready but it's worth mentioning. All you have to do is point .bashrc at the newer JDK.
Hit me back if you need help setting the variable in BASH.:guitar:

---

