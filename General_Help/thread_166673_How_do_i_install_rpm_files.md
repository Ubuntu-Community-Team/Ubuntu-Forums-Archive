---
title: "How do i install rpm files?"
date: 2006-04-26
forum: General Help
---

### Post by morbid_bean on 2006-04-26
I downloaded a movie player and its a rmp extention i wanna know how to install it using terminal or how ever you do it. please help!?

---

### Post by DoktorSeven on 2006-04-26
Always best to find a native package, but with no other choice:

sudo apt-get install alien 
sudo alien *whateverfilename*.rpm
sudo dpkg -i *[file alien creates]*.deb

---

### Post by aysiu on 2006-04-26
Or, to take out a step: ```
sudo apt-get install alien
sudo alien -i *packagename*.rpm
```

---

### Post by adamkane on 2006-04-26
First you install Red Hat. :)

---

### Post by nanotube on 2006-04-26
[QUOTE=morbid_bean]I downloaded a movie player and its a rmp extention i wanna know how to install it using terminal or how ever you do it. please help!?[/QUOTE]
tell us which movie player it is. because maybe it is already present in the repositories, so you don't even have to bother with the rpm...

---

