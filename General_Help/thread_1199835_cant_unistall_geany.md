---
title: "cant unistall geany"
date: 2009-06-29
forum: General Help
---

### Post by heyyy on 2009-06-29
i started learning java on my own and i needed an development kit
after some google i ended in geany
so i installed it but because some reasons i wanted to unistall it and install again
when i tried to reinstall it i noticed that it didnt download again the files...it just seemed to install
..but that means when i unistalled the files/packages instead of being deleted they remained of the computer

some help to understand whats going on?

---

### Post by monsterstack on 2009-06-29
> **heyyy said:**
> i started learning java on my own and i needed an development kit
after some google i ended in geany
so i installed it but because some reasons i wanted to unistall it and install again
when i tried to reinstall it i noticed that it didnt download again the files...it just seemed to install
..but that means when i unistalled the files/packages instead of being deleted they remained of the computer

some help to understand whats going on?

Apt and friends keep a cache of the downloaded packages here: "/var/cache/apt/archives" Have a look inside this folder to see .deb packages of all the software you have installed lately. If you ever want to get rid of these files, you can run

```
sudo apt-get clean
```

in the terminal.

---

### Post by heyyy on 2009-06-29
> **monsterstack said:**
> Apt and friends keep a cache of the downloaded packages here: "/var/cache/apt/archives" Have a look inside this folder to see .deb packages of all the software you have installed lately. If you ever want to get rid of these files, you can run

```
sudo apt-get clean
```

in the terminal.

thanks it worked

---

