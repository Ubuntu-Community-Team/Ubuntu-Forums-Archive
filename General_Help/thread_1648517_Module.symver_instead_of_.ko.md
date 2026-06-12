---
title: "Module.symver instead of .ko???"
date: 2010-12-18
forum: General Help
---

### Post by NeMewSys on 2010-12-18
Hi, i'm compiling a module, but instead of geting the nothing.ko i was expecting, i get 2 files Module.symver and modules.order, both empty.

This is my input:
[IMG]http://gyazo.com/76e4f6192718b36f9bcbbb78a457c803.png[/IMG]

This is what i get:
[IMG]http://gyazo.com/5ed0debfcfcd5de56f59e9fe1564689d.png[/IMG]


My Makefile is this:
[PHP]obj-m := nothing.o[/PHP]My nothing.c is this:
[PHP]#include <linux/module.h>

MODULE_LICENSE("GPL");[/PHP]

What am i doing wrong?

(I also tried this '/lib/modules/2.6.32-26-generic/build' has candidate kernel)

---

### Post by NeMewSys on 2010-12-19
Jump up.

---

### Post by NeMewSys on 2010-12-19
this has solution right?

---

