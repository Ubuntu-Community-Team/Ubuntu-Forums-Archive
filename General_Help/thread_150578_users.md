---
title: "users"
date: 2006-03-26
forum: General Help
---

### Post by gos1 on 2006-03-26
I cannot create users. I tried it both with sudo -s and system>administration> users and groups. I mean the user is created but the files in home directory does not. And also When I try to login to the user I created I get an error message. You dont have a home folder do you want to use root instead etc. and user cannot login again. How can I fix that problem  ? =

---

### Post by Ramses de Norre on 2006-03-26
System > administration > users and groups > add user choose the advanced tab and check what's behind "Home directory:" it shoud be "/home/$user" which generates a correct home folder.

Or: sudo adduser --home /home/username username

---

