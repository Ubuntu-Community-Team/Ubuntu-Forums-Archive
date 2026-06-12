---
title: "cant install software"
date: 2011-05-24
forum: General Help
---

### Post by braveheart2 on 2011-05-24
I upgraded from 10.10 to 11.04 32bit, I have installed tons of programs since the upgrade without error. I booted it today and began to install chromium from software center and this is the errors I got before it continues to install.

things I have tried: sudo apt- get update


I need assistance with this asap, thank you.

---

### Post by conradin on 2011-05-24
try
```
sudo dpkg -a --configure
```

---

### Post by yetiman64 on 2011-05-25
According to that picture you are missing the ttf-mscorefonts-installer. It is part of the ubuntu-restricted-extras package in Natty.

Try installing ubuntu-restricted-extras first and see if that helps.

---

### Post by linuxinstalledfromhdd on 2011-05-25
Here is a really nice walkthrough to install the rest of the PPAs you may need with that as well..  

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by braveheart2 on 2011-05-25
> **linuxinstalledfromhdd said:**
> Here is a really nice walkthrough to install the rest of the PPAs you may need with that as well..  

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)
thanks a million for the link, thats amazing.

> **yetiman64 said:**
> According to that picture you are missing the ttf-mscorefonts-installer. It is part of the ubuntu-restricted-extras package in Natty.

Try installing ubuntu-restricted-extras first and see if that helps.
I thought all those repository issues were going to be fixed in this release :( thanks for the info.

> **conradin said:**
> try
```
sudo dpkg -a --configure
```
didn't do anything for me.

---

### Post by linuxinstalledfromhdd on 2011-05-25
Try reviewing the walk through and see if you missed anything.  Standing by..

---

