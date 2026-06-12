---
title: "i can't install anything from Ubuntu software center"
date: 2011-05-09
forum: General Help
---

### Post by akhwat on 2011-05-09
whenever i try to install a problem, i have this error[IMG]http://img847.imageshack.us/i/screenshotrqq.png/[/IMG]

The action would require the installation of packages from not authenticated sources.

how can i slove it ?

---

### Post by Rubi1200 on 2011-05-09
Hi and welcome to the forums :-)

What packages are you trying to install?

Thanks.

---

### Post by ~Plue on 2011-05-09
Close any instances of the software center/synaptic and run from a terminal window; (after a fresh install it sometimes need to refresh the software index)
```
sudo apt-get update
```And try installing the software package again. If you get any error messages, post the output within [CODE] tags.

---

