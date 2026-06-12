---
title: "What is PLF repository?"
date: 2006-06-06
forum: General Help
---

### Post by Hoffmann on 2006-06-06
What is PLF repository? What is the difference between this repository and the backport one? Is it legal to use those repositories?

---

### Post by xXx 0wn3d xXx on 2006-06-06
[QUOTE=Hoffmann]What is PLF repository? What is the difference between this repository and the backport one? Is it legal to use those repositories?[/QUOTE]
add this to your sources.list and then sudo apt-get update:

> deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 
and it is "questionably legal to use them." ;)

---

### Post by Jucato on 2006-06-06
PLF means Penguin Liberation Front.
Here's a wikipedia entry: [http://en.wikipedia.org/wiki/Penguin_Liberation_Front](http://en.wikipedia.org/wiki/Penguin_Liberation_Front)

---

### Post by Rui Pais on 2006-06-07
Hi, 
theres a breezy and a dapper repository.

You can browse any repositories to check what they offer, go to:
[http://packages.freecontrib.org/ubuntu/plf/pool/](http://packages.freecontrib.org/ubuntu/plf/pool/) (choose you ubuntu flavor)

Essentially, they are stuff that are not GPL or even open source, mainly for dvd stuff, java, opera, realplay, skype and mp3 codecs (those and dvd stuff seems to have problem with certain country legislations...)

---

### Post by Hoffmann on 2006-06-07
[QUOTE=Rui Pais]Hi, 
theres a breezy and a dapper repository.

You can browse any repositories to check what they offer, go to:
[http://packages.freecontrib.org/ubuntu/plf/pool/(choose](http://packages.freecontrib.org/ubuntu/plf/pool/(choose) you ubuntu flavor)

Essentially, they are stuff that are not GPL or even open source, mainly for dvd stuff, java, opera, realplay, skype and mp3 codecs (those and dvd stuff seems to have problem with certain country legislations...)[/QUOTE]

I understood your explanation.
Many thanks!

---

### Post by Rui Pais on 2006-06-07
hi,
no problem. Glad i could help.

---

