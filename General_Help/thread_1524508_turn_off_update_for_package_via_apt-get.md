---
title: "turn off update for package via apt-get"
date: 2010-07-05
forum: General Help
---

### Post by e24ohm on 2010-07-05
Folks:
I am having problems with my Drupl install, which I got from the repository with apt-get.

Each time a update comes out, about once a month, my one Drupal site breaks.

How do I turn off the feature just for the Drupal packages? I am downloading the install files from drupal.com, and going with the tar.gz files.

thanks.
E

---

### Post by warfacegod on 2010-07-05
Find the appropriate package(s) in Synaptic and highlight it/them. Then on the upper left hit the Packages menu and select "Lock Version".

---

### Post by e24ohm on 2010-07-06
> **warfacegod said:**
> Find the appropriate package(s) in Synaptic and highlight it/them. Then on the upper left hit the Packages menu and select "Lock Version".
Ok thanks...is there a way to do it from the cli?

---

### Post by warfacegod on 2010-07-06
> **e24ohm said:**
> Ok thanks...is there a way to do it from the cli?

I'm sure there is but I don't know how.

---

### Post by mikewhatever on 2010-07-06
I think aptitude can do it, for example:
```
sudo aptitude hold drupal
```
...and in case you want to cancel it later:
```
sudo aptitude unhold drupal
```

---

