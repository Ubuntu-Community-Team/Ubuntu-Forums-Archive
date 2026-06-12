---
title: "permissions denied"
date: 2006-05-09
forum: General Help
---

### Post by tj54020 on 2006-05-09
as part of my sound card installation i need to make a directory and since im new to linux im not exactly sure what im doing or why it isnt working...  this is what im getting


tommy@ubuntuTJ:/usr/src$ mkdir alsa
mkdir: cannot create directory `alsa': Permission denied
tommy@ubuntuTJ:/usr/src$

how do i set the permissions so i can do this?

---

### Post by Parkotron on 2006-05-09
Root priviliges are required to create folders outside your home directory. Please see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) .

---

