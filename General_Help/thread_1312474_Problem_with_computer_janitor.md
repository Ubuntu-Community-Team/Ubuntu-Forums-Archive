---
title: "Problem with computer janitor"
date: 2009-11-03
forum: General Help
---

### Post by alphageek89 on 2009-11-03
i used computer janitor in 9.10 today and now my sound is gone.it was playing music just minutes ago.

Please tell me what details i can provide.And yes Output volume is not mute and is on 100%.

---

### Post by P4man on 2009-11-03
you should use janitor with **great** care (or better, dont use it) as it will happily remove a ton of things you really didnt want removed. Which is what happened here apparently

Try this to hopefully fix it:
```
sudo apt-get update
sudo apt-get --fix-missing install
sudo aptitude install ubuntu-desktop ubuntu-standard
```

---

### Post by Chriis on 2009-11-06
thanks, 

it answers my concern about Janitor, 
it should have more options to be more friendly to use and not be installed by default, 
so entry users don't erase needed things,

as a write this, Janitor point me 16 packages to remove,.. i will keep them anyway



chriis

---

