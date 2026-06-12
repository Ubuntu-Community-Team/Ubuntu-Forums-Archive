---
title: "Lag in Ubuntu 11.10"
date: 2012-03-31
forum: General Help
---

### Post by Exonize on 2012-03-31
Hello, this is first time im using Ubuntu and i really like it. Everything is working perfect but i got a problem that are very annoying, when I write or drag the mouse around it lag in 2-3 sec and then it stops, this is happening all the time..

What can i do to fix this?
Sorry for my bad English, im from Norway.

---

### Post by dino99 on 2012-03-31
first, check that the graphic driver is activated. From a terminal, run:

sudo jockey-gtk

which card is used and which driver is installed ? which  ram amont installed ?

To get more info, watch the logs :
- inside /home : .xsession-errors (ctrl+h to unhide it)
- /var/log/ xorg.0.log

---

