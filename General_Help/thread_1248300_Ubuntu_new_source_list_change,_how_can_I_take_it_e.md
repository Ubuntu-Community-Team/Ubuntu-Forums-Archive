---
title: "Ubuntu new source list change, how can I take it effect? Thanks."
date: 2009-08-24
forum: General Help
---

### Post by yujianhua2002 on 2009-08-24
Hi Guys:

Originally my ubuntu uses official source list as apt-get update target, obviously it is very slow, these days I find a source mirror in my own region, I want to replace original one with current mirror.

#vim /etc/apt/source.list ##using my own region source list.
#apt-get update && apt-get dist-upgrade

Although everything works OK but when I try to update a new software, it still downloads from original official websites, still slow, in fact it can be much faster if get from local regional.

Anyone who knows please share and thanks in advance.

---

### Post by renkinjutsu on 2009-08-24
it should take effect as soon as you do `sudo apt-get update` .. but ubuntu installs from whichever repository has the newer version of whatever package you're installing.

---

### Post by geirha on 2009-08-24
If it is an official mirror, you can easily switch to it from System -> Administration -> Software sources.

---

