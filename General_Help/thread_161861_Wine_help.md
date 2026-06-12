---
title: "Wine help"
date: 2006-04-17
forum: General Help
---

### Post by morbid_bean on 2006-04-17
When I try to install a certian software on my ubuntu (starcraft) when i start the installation it will give me an error "Exp1: Error 0x00000003: path not found" now what the heck can i do to fix this....I do get this error with some of my other software as well. please help.

---

### Post by stamy on 2006-09-10
It is a right problem on .wine folder.
You need to change the owner of your wine folder like this (replace 'user' with your user name):

$ sudo chown user:user -R ~/.wine

No it should work fine (i had the same problem on now i can install Warcraft III without any errors ...:D)

---

