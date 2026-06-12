---
title: "download packages"
date: 2009-10-05
forum: General Help
---

### Post by amitch88 on 2009-10-05
how  can i downlaod packages? so i can use it on different pc. like we downloads exe files on windows platform. it is because whenever i reinstall ubuntu i must download all needed softwares. and i have two pc so i need to download on both pc. my internet speed is so slow so it is very irritating to download software like netbeans or jdk or apache.

---

### Post by justleen on 2009-10-05
apt-get install --download-only <package>
apt-get install -d <package>

they will be storen in /var/cache/apt/archives/

---

### Post by CatKiller on 2009-10-05
If you're constantly re-installing Ubuntu, you're doing something wrong.

Having said that, the package archives (.deb files) are stored at /var/cache/apt/archives. If you copy the files to that location on your machine, the package manager will use those instead of downloading them again if they are the newest version available. You could set up a local repository, but it probably isn't worth doing that for just two computers.

---

### Post by amitch88 on 2009-10-05
thanks

---

