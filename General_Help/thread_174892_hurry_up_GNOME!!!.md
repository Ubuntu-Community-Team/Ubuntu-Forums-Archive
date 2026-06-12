---
title: "hurry up GNOME!!!"
date: 2006-05-12
forum: General Help
---

### Post by lindos on 2006-05-12
my system config is:
physical RAM = 128MB
hardisk = 40 GB
Ubuntu partition = 5GB
swap space = 300MB

My question is how to speed up the GNOME. Previously I was using Red hat 9 with the same config, then the GNOME was working quite fast, so how do i speed up things in Ubuntu.

---

### Post by Ramses de Norre on 2006-05-12
```
gconf-editor /apps/metacity/general
```
and check reduced_resources, that does a lot.

---

