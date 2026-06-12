---
title: "Gnome archive manager, libstdc++.so.5"
date: 2010-03-30
forum: General Help
---

### Post by Hetepeperfan on 2010-03-30
Hi everyone,

To browse through rar archives I would like to use the standard gnome archive manager. However every time I open a rar-file it conflicts me with a commandline out put:

```
rar: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```Thus I tried : 

```
-desktop:~$ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate
```still no succes has anyone got any clues??

best hetepeperfan

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
```
sudo apt-get install unrar-free
```

---

### Post by Hetepeperfan on 2010-03-30
Thanks, but unfortunately this gives me a commandline utility. Probably a good one, but I would really like to use the one provided by gnome-desktop. 

It used to work perfectly fine for me, but some how since recently I started missing the libc++5 libs..:-(

---

